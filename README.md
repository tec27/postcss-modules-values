# CSS Modules: Values

Pass arbitrary values between your module files

### Usage

```css
/* colors.css */
@value primary: #BF4040;
@value secondary: #1F4F7F;

.text-primary {
  color: primary;
}

.text-secondary {
  color: secondary;
}
```

```css
/* breakpoints.css */
@value small: (max-width: 599px);
@value medium: (min-width: 600px) and (max-width: 959px);
@value large: (min-width: 960px);
```

```css
/* my-component.css */
@value colors: "./colors.css";
@value primary, secondary from colors;
@value small as bp-small, large as bp-large from "./breakpoints.css";

.header {
  composes: text-primary from colors;
  box-shadow: 0 0 10px secondary;
}

@media bp-small {
  .header {
    box-shadow: 0 0 4px secondary;
  }
}
@media bp-large {
  .header {
    box-shadow: 0 0 20px secondary;
  }
}
```

Note that the `:` in a `@value` definition is optional as to not break Sass.

### Justification

See [this PR](https://github.com/css-modules/css-modules-loader-core/pull/28) for more background

## License

ISC

## With thanks

- Mark Dalgleish
- Tobias Koppers
- Josh Johnston

---
Glen Maddern, 2015.
