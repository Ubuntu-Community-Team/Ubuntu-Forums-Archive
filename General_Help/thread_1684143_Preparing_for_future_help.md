---
title: "Preparing for future help"
date: 2011-02-08
forum: General Help
---

### Post by aadem on 2011-02-08
Hello everyone, about a month ago i had my first experience with my OWN installation of ubuntu and within a 
week i eradicated windows from my life (save a small partition for watching movies and interacting with certain java applets and such that i havent been able to figure out just yet, or for emergencies).  Id like to now learn as much linux/unix as possible, if for nothing else my own satisfaction.    I have come to the decision that im going to take a very small slice of my 220gb ubuntu installation partition and split it off to install a more stripped down version of Linux on.  After looking around ive come to my own conclusion that i could probably learn a LOT if i manage to install freeBSD. however ive made this decision based on a very small amount of wisdom on the world of unix, so i ask you all if you think this is a good idea (please dont think i mean freebsd is the best choice i know this is a matter of opinion) and i also ask if i boot from the iso for freebsd will it have a nice install manager, and a partition tool to create my partition like ubuntu did?  ill obviously arm myself with literature and manuals.  

My last question is say i make it through the partitioning and install, will grub automatically detect 2 OS's and give me a dual boot prompt? or will that be another learning experience

---

### Post by gufide on 2011-02-08
I know a very good tutorial, but french only.. :( you con read it using google translate [http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fwww.siteduzero.com%2Ftutoriel-3-12827-traduction reprenez-le-controle-a-l-aide-de-linux.html&act=url]("http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fwww.siteduzero.com%2Ftutoriel-3-12827-reprenez-le-controle-a-l-aide-de-linux.html&act=url")

---

### Post by corncob on 2011-02-08
I got my movies, wmv's, etc playing on Ubuntu by following the instructions at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) .  It installs Java also (you need to use the TAB key to get to the OK button on the license agreement -- that threw me at first).  I also installed libdvdcss2 and libdvdread4 from System > Administration > Synaptic package manager.

---

### Post by randiroo76073 on 2011-02-08
The main thing to remember is when you boot back into Ubuntu you need to open a terminal and run:
```
 sudo update-grub2 
```
so that grub can pickup the new distro.
I've been multi-booting for several years, don't try to run more than 5(I had 23 one time) or it gets very confusing...LOL!

---

### Post by corncob on 2011-02-08
I found "Unix for the Beginning Mage" to be quite readable: [http://www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf](http://www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf)

---

