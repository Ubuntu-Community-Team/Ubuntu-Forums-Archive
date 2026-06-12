---
title: "which package installs this file on the specified path"
date: 2010-06-05
forum: General Help
---

### Post by Elie-M on 2010-06-05
/usr/share/qt4/mkspecs/default/qmake.conf

---

### Post by cogier on 2010-06-05
I don't understand the question so I can not work out what the reply might be, or even if I am able to answer it. Can I suggest that you look here [http://ubuntuforums.org/showthread.php?t=1422475]("http://ubuntuforums.org/showthread.php?t=1422475") for advice on how to present your question to better your chance of a positive result.

---

### Post by Elie-M on 2010-06-05
I'm looking for the qmake.conf that is for qt4.

the package that installs qmake.conf inside /usr/share/qt4

---

### Post by nemilar on 2010-06-05
You can find out which package a given file belongs to by running the following command:

```
dpkg-query -S [file in question]
```

In your case, try running:


```
dpkg-query -S /usr/share/qt4/mkspecs/default/qmake.conf
```

---

### Post by Elie-M on 2010-06-05
> **nemilar said:**
> You can find out which package a given file belongs to by running the following command:

```
dpkg-query -S [file in question]
```In your case, try running:


```
dpkg-query -S /usr/share/qt4/mkspecs/default/qmake.conf
```


well thx for your answer but the package isnt installed, so the command u gave doesnt work. I'm looking for the package to actually install it

---

### Post by nemilar on 2010-06-05
You can use this page to search the Ubuntu repositories:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)  (scroll down a bit)

I didn't find that exact file, but if you just search for qmake.conf, you'll get some really good hints.

---

### Post by sdennie on 2010-06-05
If "dpkg -S file" didn't give any results then the file wasn't installed by any package on your system.  It's possible that you triggered the creation of the file or that you installed something that didn't go through dpkg to install the package but, "dpkg -S file" is the definitive source of what has been installed on your machine as a .deb package.

---

### Post by ajgreeny on 2010-06-05
Probably qt4-qmake.  Try installing it, though from what I can see it does not appear to be one of the listed files in lucid, though there are other qmake.conf files in the package.
See [http://packages.ubuntu.com/lucid/i386/qt4-qmake/filelist](http://packages.ubuntu.com/lucid/i386/qt4-qmake/filelist)

---

### Post by Elie-M on 2010-06-08
> **ajgreeny said:**
> Probably qt4-qmake.  Try installing it, though from what I can see it does not appear to be one of the listed files in lucid, though there are other qmake.conf files in the package.
See [http://packages.ubuntu.com/lucid/i386/qt4-qmake/filelist](http://packages.ubuntu.com/lucid/i386/qt4-qmake/filelist)

you were right  it was the qt4-qmake package thx

---

