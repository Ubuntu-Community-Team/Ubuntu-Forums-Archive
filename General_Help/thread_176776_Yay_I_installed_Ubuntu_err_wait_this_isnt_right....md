---
title: "Yay I installed Ubuntu err wait this isnt right..."
date: 2006-05-15
forum: General Help
---

### Post by Adragontattoo on 2006-05-15
Ok so I am an almost complete noob to Linux and have been playing with Ubuntu on my Dell laptop and love it (but somehow managed to mutate Gnome and KDE into some horrible crossbreed that doesnt work right).

So after determining that I have in fact borked my Dell install I decided that I would use the Dell as a test platform and load Ubuntu on my old gaming rig and use that after I unbork the laptop.

Specs are:
p4 2.8
Gigabyte RZ series board
1 gb pc2100 
Nvidia 6600gt AGP
1 WD 30Gb drive for / and swap
1 Seagate 160gb drive for /home, swap and other mounts that I have since forgotten
1 HP Combo drive that hates life and is on its last legs.

All went well and installed (Ubuntu Breezy 5.10) until it got to the loadin screen, at that point the screen goes all garbled and renders me unable to log in.

I am assuming that I didnt pay attention and have either set the resolution incorrectly or that the 6600GT isnt playing nice with Ubuntu.  

Any suggestions on how to fix this issue?

---

### Post by mority on 2006-05-15
Try ```
sudo dpkg-reconfigure xserver-xorg
``` and set the right resolution this time.

---

### Post by localzuk on 2006-05-15
Further to this, as it is an nvidia graphics card, you should use the 'nv' driver. If this fails, try the vesa driver (this is the equivalent of 'safe mode' style graphics).

If you want to use things such as accelerated graphics on the card, take a look at [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto) as this tells you how to install the official, proprietory, drivers.

---

### Post by Adragontattoo on 2006-05-15
ok so as a quick question.. how do I swotch to terminal to run the sudo command? 

I could always try blind typing in hopes of logging in right and getting Terminal up hehe but that is something I would rather not do.

---

### Post by mority on 2006-05-15
Press CTRL+ALT+F1 to switch to terminal 1. With ALT+F7 you switch back to the X server screen.

With CTRL+ALT+F2 to CTRL+ALT+F6 you have even more terminals...

---

### Post by Adragontattoo on 2006-05-15
awesome thanks.. Hopefully I will have it up and running tonight and be good to go.

---

### Post by Adragontattoo on 2006-05-16
ok after a bunch of trying I got it working with the Vesa driver, then upgraded to I "think" the newest Nvidia driver (will check tonight).  Looks like my desktop has crashed after sitting overnight,  unlocked the screen after running it overnight and Gdesklets has locked up.  Anywhere that there was a desklet is now just a white outline.  Ctrl+alt+backspace didnt do the usual either.  I can get a terminal prompt but any Gnome UI is gone.  Once I get home I am going to try to restart the ?Xserver? but does anyone have any suggestions for things to check to see if it is a driver issue or a stability (memory MAY be bad, Ill have to test it).

---

