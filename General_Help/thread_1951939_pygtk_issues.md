---
title: "pygtk issues"
date: 2012-04-03
forum: General Help
---

### Post by Hiuhu on 2012-04-03
Am new to pygtk and am trying to learn it and everytime I write code using vim and try to execute it this is what I get:
jemoh@Hiuhu:~$ ./window.py
bash: ./window.py: /usr/bin/env/python: bad interpreter: Not a directory
what could be the problem ?

---

### Post by r-senior on 2012-04-03
The first line in your script should be:

```
#!/usr/bin/env python
```

Note the space after 'env'.

You do know that PyGTK is not under development and the way forward is to use GObject introspection?

[http://www.pygtk.org/](http://www.pygtk.org/)

That sounds hard, but it's not.

[Python GTK3 Tutorial]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html")

Probably best to ask your programming questions in Programming Talk too. You are more likely to get an answer over there.

---

