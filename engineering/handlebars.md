# Handlebars Style Guide

## Table Of Contents

* [Quotes](#quotes)
* [Multiline expressions](#multiline-expressions)
* [Line Breaks and Whitespace](#line-breaks-and-whitespace)
* [Comments](#comments)

## Quotes
Prefer double quotes to single quotes
```hbs
{{! good }}
<button {{action "doThing"}}>Do Thing</button>

{{! bad }}
<button {{action 'doThing'}}>Do Thing</button>
```

## Multiline expressions

Multi-line expressions should specify attributes starting on the second
line, and should be indented one deeper than the start of the component
or helper name.
```hbs
{{! good }}
{{x-thing
    value=blah
    options=options
    label="thing"}}

{{! bad }}
{{x-thing
  value=blah
  options=options
  label="thing"}}

{{! this will be annoying to re-indent if you rename your component }}
{{x-thing value=blah
          options=options
          label="thing"}}

```

## Line Breaks and Whitespace

It can be helpful to have a multi-line expression be on a separate line its parent HTML—particularly when merging in `git`. When needed, you can optionally use [whitespace control](http://handlebarsjs.com/expressions.html#whitespace-control) to remove whitespace before or after an expression.

Whitespace may be omitted from either side of any mustache statement by adding a `~` character by the braces. When applied, all whitespace on that particular side will be removed up to the first handlebars expression or non-whitespace character on that side.

The following example removes whitespace before and after an expression:

```hbs
<section>
  {{~content~}}
</section>
```

The following example only removes whitespace after an expression:

```hbs
<section>
  {{content~}}
</section>
```

Here we remove whitespace only between sibling items:

```hbs
<ul>
  {{#each items as |item|~}}
    <li>
      {{item}}
    </li>
  {{~/each}}
</ul>
```

To remove whitespace before and after list items, and between items, we do this:

```hbs
<ul>
  {{~#each items as |item|~}}
    <li>
      {{~item~}}
   </li>
  {{~/each~}}
</ul>
```

That also removes the whitespace before the first item and after the last one.

In the next example, we only remove space from inside the individual list items:

```hbs
<ul>
  {{#each items as |item|}}
    <li>
      {{~item~}}
    </li>
  {{/each}}
</ul>
```

## Resources
* [Handlebars Whitespace Control](https://handlebarsjs.com/expressions.html#whitespace-control)
* [Ember White Space Playground](https://emberjs.jsbin.com/nubup/1/edit?html,css,js,output)
