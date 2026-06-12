---
title: "help! Without signal after boot with LiveCD"
date: 2010-05-04
forum: General Help
---

### Post by davidtuti on 2010-05-04
Hi,

I'm booting with a usb with unetbootin my kubuntu 10.04.
The problem is that when I select default and load the splashscreen, the monitor lost signal. 
Any help please?. I'm trying to install but is impossible I can't see anything.

Many thanks and sorry for my english!

---

### Post by DomesDKG on 2010-05-04
Here's a quote from the FAQ, your problem may be related to this. See if you can't boot into recovery and run the commands.

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
Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the floppy in the bios. This has been reported as a fix to this. [https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712](https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712)

If the problem is plymouth not displaying, and a black screen from grub to gdm, this could be due to graphics drivers needing to be loaded quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787)

Plymouth is installed with 2 themes by default you can install more via synaptic.
To change themes this code is used.
Code:
sudo update-alternatives --config default.plymouth

---

