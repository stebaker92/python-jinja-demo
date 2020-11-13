
# Jinja Cheatsheet
A basic cheatsheet for the most common & helpful Jinja features


## Common Syntax
```

{% ... %} for Statements, for example:
{% set my_var = 'foo' %}

{{ ... }} for Expressions to print to the template output

#  ... ## for Line Statements

{# this is a comment, not included in the template output #}

{% macro foo() -%}

Minus will strip out any whitespace in the macro output (minus can also be used with most Jinja statements e.g.: for, block, if...)

{%- endmacro %}
```

---
## Reusable code (macros, includes, blocks)

### Variables
```
{% set my_var = 'Foo' %}
```

Variables are scoped to their block:
https://github.com/pallets/jinja/issues/330

If you need to change variables in a different scope or block (e.g. inside a for loop), look into Jinja namespaces


### Macros
```
{% macro get_hello(name) %}
{{ 'Hello' + name }}
{% endmacro %}
...
{{ get_hello('Steve') }}
```

### Importing Macros
```
{% from "macros/nav_link.html" import nav_link with context %}
{{ nav_link.render(args) }}
```

### Blocks
```
{% block my_title %} {% endblock %}
```

Will 'inject' the content inside of this block into the parent template. You can use super() to render the initial value of a block

---
## Control flow and Arrays (if, loops, arrays)

### If statements

### Loops
```
{% for foo in bar%}
{{ loop.index }}
{% endfor %}
```

### Equality
```
{% if foo is None %}
{% if foo == 'bar' %}
```

### Inline if statements 
```
{{ p.User['first_name'] if p != None else 'NONE' }}
```

### Or
```
{{p.User['first_name'] or 'My default string'}}
```

### Mapping
```
{% if "admin" in person_list_dict|map(attribute="rol") %}
```

https://stackoverflow.com/questions/52226293/jinja2-check-if-value-exists-in-list-of-dictionaries


---
## Filters
Read more about filters here:

https://www.webforefront.com/django/usebuiltinjinjafilters.html

https://svn.python.org/projects/external/Jinja-1.1/docs/build/builtins.html

### Strings
```
{{ my_list|join(', ') }}
```

--- 

## Resources
todo.

Jinja2 Docs
https://jinja.palletsprojects.com/en/2.11.x/


## Debugging tips 
todo. 

One of the most helpful tips is rendering out an expression like so:

```
'my_var' is: {{ my_var }}
<br/>
'my_var == True' is: {{ my_var == True }}
```
