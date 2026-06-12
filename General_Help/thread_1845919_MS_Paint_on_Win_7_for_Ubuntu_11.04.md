---
title: "MS Paint on Win 7 for Ubuntu 11.04"
date: 2011-09-18
forum: General Help
---

### Post by JsCoolDart on 2011-09-18
Hi, I want MS paint [preferably to one on windows 7] for Ubuntu 11.04. I do not want GIMP, or any other such programs... Kindly help me, and thanks for the same... :)

---

### Post by mikewhatever on 2011-09-18
The simple answer is, if you want a MS product, use Windows. On the other hand, if you simply dislike GIMP, try Pinta.
[http://en.wikipedia.org/wiki/Pinta_%28software%29](http://en.wikipedia.org/wiki/Pinta_%28software%29)

PS: An installation guide:[http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html](http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html)

---

### Post by texaswriter on 2011-09-18
> **JsCoolDart said:**
> Hi, I want MS paint [preferably to one on windows 7] for Ubuntu 11.04. I do not want GIMP, or any other such programs... Kindly help me, and thanks for the same... :)

MS Paint is part of a proprietary operating system. I don't know how to advise somebody to run part of a proprietary operating system. It is not a stand-alone product. Does one need to have signed a EULA to use it? 

I don't know that there is anything unique about MS Paint... any 2 bit picture editing program would do...

```

$ apt-cache search paint|grep edit
kolourpaint4 - simple image editor and drawing application
gchempaint - 2D chemical structures editor for the GNOME2 desktop
tkpaint - Versatile bitmap/pixmap editing tool

```

---

### Post by Mark Phelps on 2011-09-18
You could TRY installing Wine and then installing MSPaint (you will have to grab the mspaint.exe file from an existing Windows setup).

The Wine app page only shows older versions of MS Paint, and the most recent ones were for XP, and rated Silver at best.  The current one for Win7 has undergone MAJOR changes -- so it's likely NOT to work.

---

### Post by haqking on 2011-09-18
Gnome paint or Gnu paint in the repos, pretty close

edit: oh wait you said windows 7 paint, that one has the ribbon style bar....well Gnome paint and Gnu paint are pretty bang on the same as the original MS paint if that helps

---

### Post by texaswriter on 2011-09-21
> **haqking said:**
> Gnome paint or Gnu paint in the repos, pretty close

edit: oh wait you said windows 7 paint, that one has the ribbon style bar....well Gnome paint and Gnu paint are pretty bang on the same as the original MS paint if that helps

Oh yeah, I think I did, out of idle curiosity, run some mspaint and solitaire executables from XP or something... I forget if they worked, but I think they did if you had the right files... I guess that would be your best bet, BUT, Mspaint in Windows 7/Vista is probably written in .NET FRAMEWORK. Which means, if you can find instructions to install that into Wine, it may work, or may not. 

Here are some instructions on installing that, just click on the version necessary
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586)

If you find the mspaint executable and it is of the correct format, you could try running it in Mono. Mono is an open source version of the .net framework with the goal of natively running any .NET program on whatever platform... 
[http://mono-project.com/Main_Page](http://mono-project.com/Main_Page)

I did sort of want to reiterate my original point that it would probably be better to just to find an alternative... MSpaint has never had any feature that has made it unique or even convenient... This is my opinion of course, ymmv... I use it if I am on a Windows box. 

On Linux, I use inkscape, gimp, fspot, libreoffice draw, ... there is also kolourpaint

I always hate it when people answer a question with something other than a direct answer, but since you never qualified why you wanted to use MSPaint, I think it is appropriate to say this (but I did also try to find a solution, as did others, to your direct question). 

Anyways, good luck. 

:guitar::popcorn::KS:KS:KS:KS:KS

---

