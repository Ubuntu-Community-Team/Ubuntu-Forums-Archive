---
title: "Splash screen vertical bars"
date: 2010-05-06
forum: General Help
---

### Post by DomesDKG on 2010-05-06
I'm still getting some vertical lines through my splash screen, they are just a little darker purple than the rest of the screen, but disappear over the ubuntu logo/text/dots.  I've tried the following from the faq, which made the screen at least show up, which is wasn't doing before.  Not quite right yet though... any ideas?


Bootup/Plymouth. 
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013](https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013)

Graphical solution : [http://news.softpedia.com/news/How-t...4-140810.shtml](http://news.softpedia.com/news/How-t...4-140810.shtml)

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
Code:
gksu gedit /etc/default/grub
and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1680x1050 Save the file and run
Code:
sudo update-grub
The resolution chosen should be your monitors native resolution.

Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.
Code:
gksu gedit /etc/initramfs-tools/conf.d/splash
and add this option FRAMEBUFFER=y, save the file.
Then
Code:
sudo update-initramfs -u

---

### Post by DomesDKG on 2010-05-06
I just installed KDE, and interestingly the KDubuntu splash shows up fine...

---

