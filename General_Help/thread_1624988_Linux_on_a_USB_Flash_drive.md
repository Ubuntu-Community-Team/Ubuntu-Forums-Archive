---
title: "Linux on a USB Flash drive"
date: 2010-11-18
forum: General Help
---

### Post by searchfgold6789 on 2010-11-18
Hi.
I was wondering if there was any distribution of linux that could be installed onto a pen drive easily, that would be fast and recommendable, and preferably not KDE because my system cannot handle that well.

I need a system that I can boot from and use just exactly like a regular hard disk install, like all of my settings will be saved if I restart.

Can that be done with (x)ubuntu?

---

### Post by oldfred on 2010-11-18
I did a full install to my 16GB flash drive. It is just like installing to any other second drive. You do have to be careful to install the bootloader grub2 to the MBR of the flash drive.

How large is your flash drive? If only 4GB it will be very tight, 8 or larger works well.

Standard full install to flash or SSD:
Does not have to be encrupted.
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB)
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by searchfgold6789 on 2010-11-18
Two Gigabytes.

---

### Post by squigish on 2010-11-18
I just picked up a 16gb flash drive to use to install ubuntu, but I'm curious as to how it will work.  What will happen as far as drivers and things if I plug it in to someone else's computer, with totally different hardware?  Does the standard ubuntu install contain all the various drivers?  

Also, I'm thinking about trying to install it as a remastersys backup of my existing root partition (which is only 8gb), so that I keep all my programs and packages installed.  Does anybody have any experience with this?  

If you're interested in picking up a large flash drive on the cheap, head over to deals.woot.com; they don't sell anything there, but they have lots of links to good deals on flash drives; that's how I got mine.

---

### Post by oldfred on 2010-11-18
With 2GB you will not be able to do much. Perhaps one of the smaller versions of Linux or  a persistent install of an ISO, but you will not be able to save a lot since the ISO is 700MB.

Flash drives are slower and USB ports are slower, reading seems pretty good, writing real slow.

You can configure with generic video drivers and it should work on most systems, perhaps with a added setting on the linux line from grub menu when booting like nomodeset, xforcevesa, or others.

---

### Post by bill516 on 2010-11-18
I have done this with Ubuntu, Mint, sidux (now aptosid) and antiX.

I have done the installation as I do it on any other HD running from my USB port.  As one poster wisely said, make sure you put grub on this device or it will not boot.

I would suggest a 16 Gigabyte USB stick.  This gives you enough room for a reasonable home partition and even a small swap file if your hardware requires one.  If you have 2 Gigabytes or more of RAM on the machine(s) you plan to use you probably can dispense with the swap file.

I usually preformat the jump-drive I plan to use and I will use ext2 if the distribution does not object.  It seems to run with a bit less overhead than either ext3 or ext4.

If you plan to use this for traveling your Home partition can be much smaller than it normally is because you will transfer your data files back to your main machine when you get home.

In my application I cannot make assumptions about the machine(s) I will "borrow" to run my USB stick, so I try to avoid any proprietary drivers, especially for graphics.

When you do your installation let Grub2's os-prober run and list the system(s) on your home machine.  Very handy backup for your home Grub if you do that.

I normally run Gnome, though KDE has enough I like that I always hae Mepis on my machine.  For this application, though, look at either xfce or lxde.  They are lighter and they will work nicely in this application.

Yes, your USB stick will be a bit slower than your normal HD, but it surely does go through the airport more easily!

---

