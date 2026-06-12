---
title: "Print out installed and not installed things in Synaptic"
date: 2006-04-14
forum: General Help
---

### Post by Xecuter on 2006-04-14
Does Synaptic keep a list of packages that are available and packages that are installed somewhere? Or is it possible to get a list?

---

### Post by vruum on 2006-04-14
this is actually what synaptic does (or dpkg). in the left side pane press the "status" button at the bottom, it will let you choose which packages the main pane shows, installed, not installed, which can be upgraded etc.

---

### Post by Xecuter on 2006-04-14
Yes I know that. But I am asking for a text file (maybe, or something else) that contains a list of these packages. 

But if there is no list, is it possible to get make a list?

---

### Post by vruum on 2006-04-14
ok, sorry bout that. I looked, and the closest thing I could find was the dpkg -l command, so something like this might work
```
 dpkg -l | grep 'ii ' > installed_debs
``` for a list of installed files. but there might be more suitable command, that I just couldn't find.

---

### Post by PriceChild on 2006-04-14
Why do you need a list?

Using the update command, and then using search in synaptic lets you search for whatever you want. Packages are also sorted in almost every useful way. if you choose the categories bottom left.

---

### Post by Xecuter on 2006-04-14
I am (hopefully) going to make a program for people without internet connection, like myself, so that they can download the rigth packages and the right depending packages and so furth. That's why I need a list of installed packages.  And since I'm not the best programmer yet I'll use my time on it. 

BTW: Thanks vruum, that will do the trick. ;)

---

