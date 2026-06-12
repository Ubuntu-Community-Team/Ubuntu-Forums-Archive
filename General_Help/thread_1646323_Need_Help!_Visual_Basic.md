---
title: "Need Help! Visual Basic"
date: 2010-12-15
forum: General Help
---

### Post by Crazyatvspaz on 2010-12-15
Ok iam not new to ubuntu but iam new to anything as far as developing anything for ubuntu. Iam taking a class in community college learning how to use Visual basic for windows. I have to write an essay as to how  i liked or disliked the class. I hate windows and anything information i  can get to write something would be appreciated. Is there a program or something that would be like VB? I signed up for a LP account. I get what that is. but how does one sit down and write a new package? Please help. please dont laugh Ubuntu gods...

---

### Post by WorMzy on 2010-12-15
Are you looking for Visual Basic for Linux, something similar for developing Windows applications on Linux, or a development environment like Visual Basic for developing Linux applications?

Well, VB may be able to run on Linux with wine, but I doubt it will work well.

There's monodevelop for developing .NET applications on Linux, which can then be ported over to Windows.

And there's a number of Development Environments available for developing Linux apps. Not all of them have integrated UI developers, but some do. Netbeans and Eclipse are good for developing Java apps, and can be used for other languages too; there's Anjuta for C/C++ development, which comes with a GTK UI developer (Glade) built in; and there's PIDA for python development. There's plenty more about too, check the Software Centre.

---

### Post by Crazyatvspaz on 2010-12-15
iam not looking to run VB on Ubuntu but rather development software specifically for Ubuntu or Linux in general.

---

### Post by squenson on 2010-12-15
I would recommend that you look at Python which is running on Windows and Linux. There are several Integrated Development Environment from the simplest (IDLE) to the most sophisticated (I let the Python gurus put a name here).

---

### Post by alexfish on 2010-12-15
Don't for get some grass roots stuff

tcl/tk

most linux systems have it

on ubuntu can be called up : tclsh

then a programmable window / widgets 

wish

calls up standard default 

or depending if on system 

wish8.4
or
wish8.5

tons of info and how to's  on the web

show your tutor that one /  license included;;;;;)

Added had to check if this worked on 10.10

wish widget

---

### Post by todak on 2010-12-15
[Gambas]("http://gambas.sourceforge.net/en/main.html") is in the repositories. Gambas Almost Means Basic. ;)

---

### Post by rg4w on 2010-12-15
Real Software makes REALBasic for Linux, in addition to Mac and Windows.  Not FOSS, but maybe a good way to leverage your VB skills.

I enjoy LiveCode from RunRev.com a lot, another non-FOSS multi-platform dev tool.  Not quite like VB, but very high level and GUI-centric.

But unless you're looking to use a VB-like system, Python makes a good choice and you can't beat the price. :)

---

### Post by kalaharix on 2010-12-19
IMHO ex-VB6ers expect a more integrated drag 'n drop gui environment that Python can offer. Debatable whether thats a good or bad thing but that's the way it is.

Gambas really is very good software though the documentation is not pitched at newbies. The transition from VB6 is not plain sailing: Gambas is much more oop with as much similarity to Java as VB6.

This is a transition time with Gambas2 available in most repositories and Gambas3 in a sort of extended pre-Alpha stage. There are quite a few changes from Gambas2. The new Gambas3 is stable but subject to change.

The best way to get Gambas2 from Ubuntu is to open a terminal and type 'sudo apt-get install gambas2'. The repository install from software centre is incomplete.

Gambas3 can, at this stage, only be compiled from source and full instructions including dependencies are on the Gambas website.

What I am saying is that if you think this might be the way to go then perhaps you should start with Gambas3. I personally find it difficult to move from one version of a software product to another (remembers: dBaseIII to dBaseIV: yaaarrgggh!)

---

