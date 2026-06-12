---
title: "Adding functions to Python"
date: 2009-07-19
forum: General Help
---

### Post by blazemore on 2009-07-19
I've written a function which I use a lot in Python.
How can I use this in other projects via importing?

either by 1) adding it to the math module
or 2) creating a new module

the function is called isprime(n)

---

### Post by unutbu on 2009-07-19
Make a module call something like utils_math.py

Place the function definition there:
```

def isprime(n):
    ...

```
Place the utils_math.py file in a directory which is in your PYTHONPATH. For example, if you've defined your PYTHONPATH environment variable like this:
```

% echo $PYTHONPATH
/home/user/pybin

```
Then place utils_math.py in ~/pybin.

Then you can use isprime() in other Python scripts like this:
```

import utils_math.py
utils_math.isprime(n)
```

or
```

from utils_math.py import isprime
isprime(n)
```

---

### Post by bobince on 2009-07-19
Agreed on putting it in a module.

You don't necessarily have to fiddle with $PYTHONPATH (or sys.path) though; in Ubuntu there is already a user-specific directory path you can create (if it's not there already) and put user modules in, namely:

    /home/you/.local/lib/python2.6/site-packages/

(adjusting ‘you’ and ‘2.6’ as necessarily...)

---

### Post by blazemore on 2009-07-21
Great thanks for your help. I'm specially interested in maths programming with Python, and I'm teaching myself as I go along. This is very useful.

---

