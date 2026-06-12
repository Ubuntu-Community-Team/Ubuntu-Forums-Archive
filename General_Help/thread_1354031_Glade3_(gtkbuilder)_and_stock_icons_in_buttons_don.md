---
title: "Glade3 (gtkbuilder) and stock icons in buttons dont show in 9.10"
date: 2009-12-13
forum: General Help
---

### Post by Patagon on 2009-12-13
Hello,

I have a problem showing the icons (image or stock icons) in glade3 (glade 3.6.7 installed from synaptic or compiled from sources in english and also spanish dont work, gtkbuilder project and gtk+ 2.16).

With gtk+ 2.16 only show icons inside a toolbutton, but dont show icon or image icon in a button.

I do not think it's a lang problem.

[IMG]http://img205.imageshack.us/img205/331/imgle.png[/IMG]


> Data:
Linux name 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux



This worked fine in ubuntu 9.04


Bye

---

### Post by jordilin on 2009-12-17
I've got the same problem, if nobody answers we will have to fill in a bug I'm afraid.

---

### Post by shingalated on 2009-12-17
I've got the same thing here.  Glade 3.6.7 on Ubuntu 9.10

---

### Post by AndThenWhat on 2009-12-19
This is DEFINITELY a bug.  I don't know how to file one, but this really sucks and needs to be fixed ASAP!

---

### Post by Patagon on 2009-12-19
I already reported the bug on Launchpad
[https://bugs.launchpad.net/ubuntu/+source/glade/+bug/498473](https://bugs.launchpad.net/ubuntu/+source/glade/+bug/498473)

I thought it was some settings, maybe this error has to do with the 
theme.

You can also report it at the following address:
[https://bugs.launchpad.net/ubuntu/+source/glade](https://bugs.launchpad.net/ubuntu/+source/glade)
Topic: "Glade3 (gtkbuilder) and stock icons in buttons dont show in ubuntu 9.10"


Bye

---

### Post by Patagon on 2009-12-26
This is the response from Javier Acuña Ditzel in launchpad

> Try this:
1. Open gconf-editor
2. Browse to dektop/gnome/interface
3. Check "buttons_have_icons"


This fix the error.

Bye

and Happy Holidays!

---

