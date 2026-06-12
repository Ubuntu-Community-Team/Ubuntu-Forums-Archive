---
title: "does anyone find java software like vuze/Jdownloader to be really slow?"
date: 2010-10-05
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-05
I have the following spec:
- Intel Core 2 Duo 1.86Ghz
- 4GB Ram
- 1TB Hard Disk
- 256MB Nvidia GeForce Graphics Card

I believe my system is quite fast, yet programs like JDownloader and Vuze (aka azureus) are very slow. More so on the GUI side, not so much program functionality (although I have not tested this either). If I scroll down a list of items, it takes ages, it lags and response time is quite bad.

Does anyone else have this issue?

Also, I have two java processes running, each using 200MB of memory. I am assuming one is for Vuze and the other is for Jdownloader. 

It seems to me that Windows XP/Windows 7 ran java applications much faster and had less ram. I definitely see that with Vuze as it never went into the 200MB area when under windows.

---

### Post by lykeion on 2010-10-05
I don't use either of these programs myself. But apparently there are some GUI options in JDownloader to increase performance:
[http://jdownloader.org/changes/version/version-0.5.859#performance](http://jdownloader.org/changes/version/version-0.5.859#performance)

Vuze has also some Interface options. Maybe switching to Classic will increase performance? Also disabling some plugins (like azemp, azbuddy) may help.
[http://wiki.vuze.com/w/The_Azureus_Experience](http://wiki.vuze.com/w/The_Azureus_Experience)

---

### Post by apoth on 2010-10-05
I use Vuze (advanced) on a relatively slow laptop without any issues at all.

Check the JVM it's using is a recent Sun version 1.6.

---

### Post by fuzzylogic25 on 2010-10-18
i have done all that and its still really slow. but note that its only the graphics end that is slow. the functionality is still really fast. its downloading heaps of torrents at full speed.

but simple things like scrolling down a list of 40 torrents is slow. i found this link however:

[http://ubuntuforums.org/archive/index.php/t-1129187.html](http://ubuntuforums.org/archive/index.php/t-1129187.html)

but dont know where my vuze script file is in order to change it. but basically that first post (which is all you need to read) says you need to turn on openGL for the java application. It gives instructions but i cant find the required file. If anyone can help me that would be great!

---

### Post by mister_playboy on 2010-10-18
It's not your computer... slowness (especially in terms of startup) is just inherent to the nature of Java virtual machines.  The ability of these programs is worth the hassle, however.

---

