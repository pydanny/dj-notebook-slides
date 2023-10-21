---
title: Reveal-md
theme: blood  # black, white, league, beige, sky, night*, serif, simple, solarized, blood, moon
revealOptions:
  transition: slide
margin: 0.04
---

# [django](https://djangoproject.com)
# ➕
# [Jupyter](https://jupyter.org/)

The story and demo of [dj-notebook](https://github.com/pydanny/dj-notebook)

---

## Table of Contents

1. Story
2. Demo
3. Calls to action

---

## 1. Story

---

### Jupyter Notebook is awesome

- Easy visualizations
- unlike the REPL remembers state between sessions

---

### Jupyter buts...

- The web interface feels clunky
- Who wants to code in a browser?

---

### django-extensions
## shell_plus
### is awesome

- Loads models, settings, and more into Django shell
- Further enhances the shell with ipython, bython, etc

**note: Calling it shell_plus from now on**

---

### shell_plus buts...

  - Tied to all the other pieces of django-extensions
  - Code is a bit cryptic
  - Shell doesn't remember what you did before

---

## [Django+Jupyter]()
### is wonderful

So easy! 

```sh
./manage.py shell_plus --notebook
```

Even brings in shell_plus!

---

# But...

---

## [Django+Jupyter]() never works

---

### After periodic attempts over the years

---

## I gave up on [Django+Jupyter]()

---

# June 2023

---

Audrey started to use Jupyter notebook but wasn't complaining

---

Taught me that VS Code has a fantastic interface

---

Still couldn't use it with Django :sad:

---

# July 2023

---

Found example in Kraken for running Django with Jupyter

```python
import localdev.jupyter.setup
```

---

Then I could do this:

```
from octoenergy.data.brands.models import Brand
Brand.objects.all()
```

```
<QuerySet [<Brand: Octopus Energy>,
<Brand: Two Scoops Energy>]>
```

:shock:

---

## What about django-extensions shell_plus?

I want that magic shell...

---

### Dove into shell_plus

```python
# django_extensions/management/shells.py
for directive in import_directives:
    if isinstance(directive, str):
        directive = directive.strip()
    try:
        if isinstance(directive, str) and directive.startswith(("from ", "import ")):
            try:
                node = ast.parse(directive)
            except Exception as exc:
                if not quiet_load:
                    print(style.ERROR("Error parsing: %r %s" % (directive, exc)))
                    continue
            if not all(isinstance(body, (ast.Import, ast.ImportFrom)) for body in node.body):
                if not quiet_load:
                    print(style.ERROR("Only specify import statements: %r" % directive))
                continue
```

---

### Got it working!

```python
%run localdev/jupyter/setup_plus.py
```

```python
_plus.Brand.objects.all()
```

```
<QuerySet [<Brand: Octopus Energy>,
<Brand: Two Scoops Energy>]>
```

---

### Getting there took a while

- Code was one challenge
- Kraken's magnificent volume was another

---

## I
## want
## to move
# [faster]()

---

### I want to move faster

- Kraken serves 10s of millions of customers
- We have to tread carefully

---

## Let's extract the code from Kraken!

---

# Open sourcing

---

## Open sourcing

- Allows us to add features more quickly
- Share the fun of Django+Jupyter with everyone else

---

### Good Fortune

Django+Jupyter is not tied to Kraken or Octopus Energy's business model

---

## Current state:

- Easy-to-use wrapper around shell_plus
- Extra tools added that we've dreamed up

---

## 2. Demo

---

## 3. Calls to action 

---

# Try dj-notebook

- Opinions
- Tricks
- Bugs
- Features

---

## Help us fight climate change

---

### [octopus.energy/careers](https://octopus.energy/careers)

---

# Work for others in the field

TODO list climatebase

