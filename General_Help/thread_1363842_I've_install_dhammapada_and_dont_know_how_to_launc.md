---
title: "I've install dhammapada and dont know how to launch it"
date: 2009-12-25
forum: General Help
---

### Post by ivanhoe75 on 2009-12-25
No item in menus, I didnt find executable, doc, man for it

---

### Post by 3rdalbum on 2009-12-25
$ apt-cache show dhammapada
W: Unable to locate package dhammapada
E: No packages found

How did you install it? If you installed it from a repository using Synaptic or apt-get (or using a Debian package) you can find the the package in Synaptic, right-click it, go to Properties and Installed Files. Anything inside /bin, /usr/bin or /usr/local/bin can be run.

If it didn't install any menu items, then it's probably a command-line program.

---

### Post by bodhi.zazen on 2009-12-25
It is display-dhammapada =)

It is command line:

```
display-dhammapada
```

You can get it to display in X with

```
xdhamma
```


See man display-dhammapada for additional options (it is short).

If you wish to use it in X, create a launcher =)

---

