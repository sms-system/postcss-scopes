# postcss-cscopes

A PostCSS plugin that automagc adds scopes to CSS

## Features

- Nested scopes
- Support for pseudo-elements on scoped elements
- Global classes inside the scopes, using `global` attribute
- Automatic html recomposition, which doesn't break initial code
- Easy integration into an existing project

## Example

Imagine that you have HTML like this:

```html
<div class="title">Main title</div>
<div class="block">
  <div class="title">Block Title</div>
</div>
```

and CSS:

```css
.title {
  background: #da9a9a;
}
.block .title {
  color: #da9a9a;
}
```

If we try to display this markup, we get a problem:

![Without scopes](https://raw.githubusercontent.com/sms-system/postcss-scope/master/img/without_scopes.png)

`.block .title` inherited styles from root .title, but we don't want this.

**And what to do ?**
  
Just add attribute `scoped` to element with class `.block`,

```html
<div class="title">Main title</div>
<div class="block" scoped>
  <div class="title">Block Title</div>
</div>
```

and all classes inside it automagically become isolated.

![Without scopes](https://raw.githubusercontent.com/sms-system/postcss-scope/master/img/with_scopes.png)

After the transformation HTML and CSS become like this:

```html
<div class="title">Main title</div>
<div class="block">
  <div class="title_scope1">Block Title</div>
</div>
```

```css
.title {
  background: #da9a9a;
}
.block .title, .block .title_scope1 {
  color: #da9a9a;
}
```

## Support

Please [open an issue](https://github.com/sms-system/postcss-scope/issues/new) for support.