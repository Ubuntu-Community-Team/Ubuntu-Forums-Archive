---
title: "Can¿t use highgui module from opencv in python"
date: 2009-11-25
forum: General Help
---

### Post by sephirot_5 on 2009-11-25
I'm using opencv to do some pattern recognition on images, for a very important school project. The language used is python (because i want to focus on getting the app to do what it needs to do, not to worry about handling memory leaks in c++...) and today i installed all opencv related packages I found in the repos (including the python wrappers).

I was trying to test some simple algorithms, when i came across this error:

```

$ python prueba.py
Traceback (most recent call last):
  File "pureba.py", line 9, in <module>
    img = highgui.cvLoadImage(argv[1])
NameError: name 'highgui' is not defined

```

I understand there's a highgui module on opencv for python (just like in standard c++ opencv), then why can't i import it? I need your help oh great benevolent Ubuntu wizards :)

---

### Post by sephirot_5 on 2009-11-25
Come on, please help me, I can't find a solution to this problem and I really don't want to code on Windows. ):

---

