---
title: "scanner     root permissions needed to modify"
date: 2010-10-18
forum: General Help
---

### Post by choochoousmc on 2010-10-18
simple scan and x sane don't scan
Sends signal to scanner and scanner control panel (on scanner) lights up, but does nothing.
simple scan gives warning failed to communicate
x sane just closes

using Epson nx510 all in one as a wireless      printer works on wireless just fine.

Meerkat sticky notes tells how to modify the conf file.
But I need to have root permissions.

How do I get root permissions  so I can modify files!

---

### Post by P4man on 2010-10-19
press alt+F2 (or open a terminal) and type

```
gksudo gedit
``` 

or

```
gksudo gedit /path/to/file
```

That will open a text editor with root permissions. You can open the file in it, modify it and save it.

---

### Post by browntiger on 2010-10-23
Hi, I am new here.  I have an Epson NX515 on a USB port. I am using Ubuntu 10.10 x64.  I tried Xsane, simple scan, and all I got was 'scanner not found.'  I checked the Ubuntu official documentation, tried everything there. The printer works fine, but no scanner. I solved the problem by buying VueScan.  $39.95 later, and my scanner works beautifully. I hope that this helps.

---

