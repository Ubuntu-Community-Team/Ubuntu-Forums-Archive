---
title: "icewm customisation"
date: 2006-04-11
forum: General Help
---

### Post by GoodPanos on 2006-04-11
Does any one know how to add shortcuts to programs on the icewm desktop?  Also what if I want to add more programs on the drop down menu?

---

### Post by Ramses de Norre on 2006-04-11
I don't know/use icewm but can't you just use ln -s to make symlinks for the shortcuts?

---

### Post by GoodPanos on 2006-04-11
> ln -s to make symlinks I'm not sure I understad what you are talking about.

I want to put for instance the Firefox icon on the desktop so I can execute directly from there.

---

### Post by az on 2006-04-11
Icewm does not provide a desktop in that sense.

You can install and run rox-filer.  If you start it with the -p=1 option, you get a "pinboard" for links like that.  It will not be a desktop in the sense that the gnome or KDE desktop is a seperate folder, but it is probably what you are looking for.  It is quite fast on older hardware.


You can add

rox -p=1

to the /.icewm/startup
script.  If there is an executable script there, it gets run every time you start icewm, so that's what you want.

---

### Post by sendgift2008 on 2006-04-11
:mad: [QUOTE=GoodPanos]Does any one know how to add shortcuts to programs on the icewm desktop?  Also what if I want to add more programs on the drop down menu?[/QUOTE]
[[img]http://www.top22.cn/QQCF_Pic/QQCf_Style12.gif[/img]](http://www.top22.cn/qqcf.asp?46.sendgift2050)

---

### Post by GoodPanos on 2006-04-12
* /.icewm/startup* where is this file located?  Is it in the root?

---

### Post by az on 2006-04-12
[QUOTE=GoodPanos]* /.icewm/startup* where is this file located?  Is it in the root?[/QUOTE]

In your home directory.

---

### Post by GoodPanos on 2006-05-22
Rox rocks :) 

Is there a way to customize the mouse pointer (cursor)?  I got a 1680x1050 resolution and the mouse pointer is pretty small.

---

