---
title: "Google Earth Font Style"
date: 2011-05-17
forum: General Help
---

### Post by coldcrow on 2011-05-17
I recently installed Ubuntu 11.04, and Google Earth 6.  When I started Google Earth the GUI text is stretched out and difficult to read.  I included an image of what it looks like.  I tried to change the GoogleEarthPlus.conf, but I didn't see anything else about GUI settings.  I tried to add them myself but that didn't work.  Any suggestions?  Fix?

[http://img.photobucket.com/albums/v497/coldcrow/Screenshot.jpg](http://img.photobucket.com/albums/v497/coldcrow/Screenshot.jpg)

---

### Post by coldcrow on 2011-05-17
For anyone else who has the same problem, this solution solved it for me.
[http://www.google.com/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en)

---

### Post by shashanksingh on 2011-05-18
> **coldcrow said:**
> For anyone else who has the same problem, this solution solved it for me.
[http://www.google.com/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en)

+1
for problem and solution.

):P

---

### Post by shashanksingh on 2011-05-18
What I do not get is that if google released a version for linux, why didn't it use open-source fonts???

---

### Post by samMD on 2011-05-19
I have the same problem ;/

sudo apt-get install ttf-mscorefonts-installer


this is the output after the cmd above:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libglademm-2.4-1c2a libapr1 libgconfmm-2.6-1c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by samMD on 2011-05-19
I solved this issue via this thread: 

[http://ubuntuforums.org/showthread.php?p=10838498#post10838498](http://ubuntuforums.org/showthread.php?p=10838498#post10838498)

I followed these instructions :

> **ElrohirMacBeorn said:**
> I had the same problem and solved it a minute ago: 
the missing fonts are the microsoft-core-fonts (arial, times, etc...). Since the package ttf-mscorefonts-installer has been installed, they should have been available, but my font-installation-module told me otherwise. 

Simple removing and reinstalling ttf-msocorefonts-installer solved the problem

```
sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer 
```

---

### Post by gccradioscience on 2011-07-11
[SIZE=2]I am having the same problem as you are having.  I have a problem with this hard to read font called "atari" which came out of the font libraries through ubuntu.   I wish there was a way to change the font from atari to arial or something better on the google Earth menu.  I need help here.  :confused:[/SIZE]

---

