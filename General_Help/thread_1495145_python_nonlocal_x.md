---
title: "python nonlocal x??"
date: 2010-05-27
forum: General Help
---

### Post by oleink on 2010-05-27
```
#!/usr/bin/python
# Filename: func_nonlocal.py
def func_outer():
    x = 2
    print('x is', x)
    def func_inner():
        nonlocal x
        x = 5
    func_inner()
    print('Changed local x to', x)
func_outer()

```

When I have this code in python why does it print:
x is 2
Changed local x to 5

What I mean is what does nonlocal x actually do by all I can see you are setting a local x with x = 5??

---

### Post by oleink on 2010-05-27
I guess one of my main questions is how is it different and/or similar to global x?

---

### Post by oleink on 2010-05-27
any answers?

---

### Post by lisati on 2010-05-27
From [http://www.python.org/dev/peps/pep-3104/](http://www.python.org/dev/peps/pep-3104/)
> In most languages that support nested scopes, code can refer to or rebind (assign to) any name in the nearest enclosing scope. Currently, Python code can refer to a name in any enclosing scope, but it can only rebind names in two scopes: the local scope (by simple assignment) or the module-global scope (using a global declaration).

This limitation has been raised many times on the Python-Dev mailing list and elsewhere, and has led to extended discussion and many proposals for ways to remove this limitation. 

Clear as mud? I'm not a python programmer....

---

### Post by oleink on 2010-05-27
> **lisati said:**
> From [http://www.python.org/dev/peps/pep-3104/](http://www.python.org/dev/peps/pep-3104/)


Clear as mud? I'm not a python programmer....

Well according to that I'm pretty sure I understand it now

ps thanks for your response

---

