---
title: "How to run a .bat file? [NEED SERIOUS HELP]"
date: 2009-11-19
forum: General Help
---

### Post by Khodan on 2009-11-19
Hello community,
i used to use windows till my windows blowed up so i downloaded ubuntu.
I used to play at windows runescape private servers,
you can play them by downloading cache and running the .bat file.
Well you can't here and i searched the forums for solutions but it didnt help me.
If you guys can help me it would be awesome!
If i run the .bat this will show up:
[SIZE=4][COLOR=Red]@echo off 
Title Heaven-Pkz CMD 
cd Heaven-Pkz 
Start JAVAW -Xmx400m -cp .;Theme.jar Gui 0 0 lowmem members 32 
exit[/COLOR][/SIZE]

Help me please?
Thank you Ubuntu community!

---

### Post by justleen on 2009-11-19
You cant just run a (dos/windows) batch file... 
Either you have to port it to bash, or use wine to run it.

---

### Post by Khodan on 2009-11-19
> **justleen said:**
> You cant just run a (dos/windows) batch file... 
Either you have to port it to bash, or use wine to run it.
Well you see,
im new to Ubuntu.
Running it with wine doesn't work and how do i port it?

---

### Post by Terrycymru on 2009-11-19
This page may help you convert a .bat file:

[http://tldp.org/LDP/abs/html/dosbatch.html](http://tldp.org/LDP/abs/html/dosbatch.html)

---

### Post by Sin@Sin-Sacrifice on 2009-11-19
[http://www.google.com/#hl=en&source=hp&q=runescape+private+servers+ubuntu&aq=f&aqi=&oq=&fp=5b7cf21b103219ea](http://www.google.com/#hl=en&source=hp&q=runescape+private+servers+ubuntu&aq=f&aqi=&oq=&fp=5b7cf21b103219ea)

---

### Post by billy192 on 2010-12-31
Hi,
as you will guess i am new to this Ubuntu stuff. 
what is run it with wine?

Many thanks
Niel

:confused:

---

### Post by Chronon on 2010-12-31
WINE is a recursive acronym for (W)INE (I)s (N)ot an (E)mulator.  It is actually an implementation of WinAPI that allows programs written for Windows to run on Linux, BSD, OSX, &c..  Support isn't complete so some programs will work fine while others will not.

There's a database with reports on many windows programs here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Khodan:
The relevant line that you posted is this:
```
JAVAW -Xmx400m -cp .;Theme.jar Gui 0 0 lowmem members 32 
```

It looks like it's trying to run the named Theme.jar file, so you could try this instead: 
```
cd Heaven-Pkz 
```
then
```
java -jar Theme.jar
```
This should at least try to run the program and should give some error messages if it fails.

---

