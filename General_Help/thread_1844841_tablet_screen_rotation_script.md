---
title: "tablet screen rotation script"
date: 2011-09-15
forum: General Help
---

### Post by dbowlin17 on 2011-09-15
hi there!

got a Fujitsu T4020D tablet here, and before I upgraded to 11.04, I was using Xournal to take notes and write on pdfs. I still use that program and all, but the screen rotation script that I had doesn't work properly anymore. the display still rotates, however, when I use my pen the mouse doesn't respond even remotely close to the region I am directing my pen. However, when I use the script to rotate the screen back to normal, the pen works without any flaws. 

Have you any suggestions as to how I could use a better/different sh script to allow me to use my tablet in portrait mode?

---

### Post by Favux on 2011-09-16
Hi dbowlin17,

Natty's default xf86-input-wacom-0.10.11 has a bug with cw and ccw rotation swapped.  That's been fixed upstream so you can either upgrade your xf86-input-wacom or you could just change your script and substitute cw for ccw or the reverse.

---

### Post by dbowlin17 on 2011-09-24
hey, I searched in synaptic for all the things with wacom in them, and all i found was 1:10:11-0ubuntu4 xserver-xorg-input-wacom

not the one you suggested upgrading... any ideas?

---

### Post by Favux on 2011-09-24
Hi dbowlin17,

The Ubuntu package xserver-xorg-input-wacom contains xf86-input-wacom-0.10.11, which is where it gets its number from.

You can either download and compile the xf86-input-wacom-0.11.1 tar or clone the git repository.  That's part II. b) and c) on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Or the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") tells you how to clone the git.

FYI Oneiric has the same bug since it has xf86-input-wacom-0.11.0.  I finally posted a Launchpad bug report on it so hopefully they'll fix Oneiric.  And if we're real lucky backport the patch into Natty?

---

### Post by dbowlin17 on 2011-09-25
hey, thanks. wasn't able to get it to work, despite not getting any error messages. oh well, thanks for your help.

---

