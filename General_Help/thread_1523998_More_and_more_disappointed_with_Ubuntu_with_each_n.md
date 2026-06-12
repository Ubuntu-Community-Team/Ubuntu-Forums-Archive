---
title: "More and more disappointed with Ubuntu with each new release.."
date: 2010-07-04
forum: General Help
---

### Post by Amurko on 2010-07-04
I started using Ubuntu in 2006 and it provided me with pretty much all the functionality I needed with a very intuitive interface and and organization (esp the package system.)  I replaced all my windows installations with Ubuntu and never looked back..

I consider myself a somewhat computer savvy user but with each new release, I've encountered numerous problems that severely disrupt the normal functionality of a basic OS and cannot be solved in a straight-forward manner.  Some example I'll list:

1) GRUB.  I got a new Dell Laptop with Windows 7 and I wish to dual boot.  OK.  So I repartition and install Ubuntu 9.10.  OK, so far so good.  When Lucid came out, I upgraded.  Then I reboot and I'm greeted with garbled letters instead of the usual GRUB screen.  So far, I have not been able to resolved this issue other than to use the live CD to boot and/or use Supergrub to manually boot to Linux or Windows.  I'm now dependent on this CD to properly boot my system EVERY TIME.  I've even tried reinstalling GRUB after successfully booting using the CD but grub still refuses to return (now I'm greeted with "Missing Operating System" if I'm not booting using a CD.)

2) WiFi.

The only internet access available at my apartment is WiFi.  Unfortunately, wifi does not work out of the box on my system.  Downloading the third-party drivers to get wifi working REQUIRES an active internet connection (lame catch-22 situation.)  So I'm forced to plug into the wired ethernet connection at my workplace instead every time I need to reinstall and restore my internet connection.  With so much of the world converting to WiFi, it really makes sense to have access to WiFi after installing from CD.

I don't care if I have to download a much larger CD filled with tons of useless junk; if anyone know of any sort of "expanded version" of the Ubuntu installation cd with a greater variety of WiFi drivers included so I don't have to go through this lame and convoluted procedure just to get my Wifi working every time a reinstall is necessary, I would need it ASAP!

---

### Post by J V on 2010-07-04
Ubuntu updated to grub 2 in 9.10, you need to reinstall it and the MBR... [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You don't have to download the driver every time you want to connect, just do it once, install, and you can use the network, whats the problem?

---

### Post by Amurko on 2010-07-04
> **J V said:**
> Ubuntu updated to grub 2 in 9.10, you need to reinstall it and the MBR... [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You don't have to download the driver every time you want to connect, just do it once, install, and you can use the network, whats the problem?

I have tried literally everything under the sun at that site to get Grub to work again but it still doesn't.  What can I do to generate more debugging info?

---

### Post by J V on 2010-07-04
I don't know, but if I were you, I'd save my home partition, a list of installed packages, and completely reinstall ubuntu fresh, restore the packages and the home partition, and it will work...

---

### Post by Amurko on 2010-07-04
> **J V said:**
> I don't know, but if I were you, I'd save my home partition, a list of installed packages, and completely reinstall ubuntu fresh, restore the packages and the home partition, and it will work...


I've done THAT too and it still doesn't restore GRUB (STILL need that CD to boot.)

---

### Post by J V on 2010-07-04
Wow that's strange... have you tried botting without the quiet mode?

(Press E over the grub selection then delete the word quiet and press ctrl x)

Is it something like this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/443105](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/443105)

---

### Post by bartman on 2010-07-04
Think about downgrading to GRUB version 1. I've experienced unexplained difficulties with the new one as well and it just isn't worth the hassle as it even isn't software depended on by other packages.

---

### Post by Rubi1200 on 2010-07-04
> **Amurko said:**
> I started using Ubuntu in 2006 and it provided me with pretty much all the functionality I needed with a very intuitive interface and and organization (esp the package system.)  I replaced all my windows installations with Ubuntu and never looked back..

I consider myself a somewhat computer savvy user but with each new release, I've encountered numerous problems that severely disrupt the normal functionality of a basic OS and cannot be solved in a straight-forward manner.  Some example I'll list:

1) GRUB.  I got a new Dell Laptop with Windows 7 and I wish to dual boot.  OK.  So I repartition and install Ubuntu 9.10.  OK, so far so good.  When Lucid came out, I upgraded.  Then I reboot and I'm greeted with garbled letters instead of the usual GRUB screen.  So far, I have not been able to resolved this issue other than to use the live CD to boot and/or use Supergrub to manually boot to Linux or Windows.  I'm now dependent on this CD to properly boot my system EVERY TIME.  I've even tried reinstalling GRUB after successfully booting using the CD but grub still refuses to return (now I'm greeted with "Missing Operating System" if I'm not booting using a CD.)

2) WiFi.

The only internet access available at my apartment is WiFi.  Unfortunately, wifi does not work out of the box on my system.  Downloading the third-party drivers to get wifi working REQUIRES an active internet connection (lame catch-22 situation.)  So I'm forced to plug into the wired ethernet connection at my workplace instead every time I need to reinstall and restore my internet connection.  With so much of the world converting to WiFi, it really makes sense to have access to WiFi after installing from CD.

I don't care if I have to download a much larger CD filled with tons of useless junk; if anyone know of any sort of "expanded version" of the Ubuntu installation cd with a greater variety of WiFi drivers included so I don't have to go through this lame and convoluted procedure just to get my Wifi working every time a reinstall is necessary, I would need it ASAP!

I can't help you with the WiFi issues, but maybe with GRUB.

Click on the link at the bottom of my post. 

Follow the instructions there and post the results back here.

Hopefully, we can help you resolve the GRUB issue.

---

### Post by philinux on 2010-07-04
OP,

Run this and post back the results.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Also see the general help forum sticky post 2.

---

### Post by bumanie on 2010-07-04
Just a thought; have you zeroed the drive before trying to reinstall? Of course, back up important stuff first. Occasionally remnants of things are left behind and cause issues that a simple format does not remove. 
Ever thought of trying another boot loader such as [GAG]("http://gag.sourceforge.net/")?

---

### Post by Amurko on 2010-07-04
Also,  it would be nice if there existed a program (preferably with a GUI) that'll run on an Ubuntu computer with a working internet connection and help download all the necessary files onto a USB disk for the purpose of getting another computer's Wifi connection working.

---

### Post by J V on 2010-07-04
[https://help.ubuntu.com/community/InstallingSoftware#Use%20Keryx](https://help.ubuntu.com/community/InstallingSoftware#Use%20Keryx)

---

### Post by Amurko on 2010-07-04
That's a nice program.. unfortunately, I would probably need something that works more directly..

I depend on using the System->Administration->Hardware Drivers thing to get my wifi working every time I reinstall.  Unfortunately, it doesn't interface with any of the offline downloaders; however if it has a wired connection available, it does its job by detecting the right Wifi drivers and downloading them.

Ideally, I would need a program that can automatically detect and download the right Wifi drivers onto a USB drive.

---

### Post by ajgreeny on 2010-07-04
Where are you installing grub when and if you are asked the question by the installer?   I do not dual boot so it automatically goes on to the main disk MBR, but I understand that the installer for 10.04 suggests you put grub on to a partition instead of, or as well as the MBR of a disk.

On the assumption that you can actually boot to your installed ubuntu, I suggest that you do so, then run ```
sudo grub-install /dev/sda
``` which will put grub on the MBR of disk1.  Use /dev/sdb if you want it on a second disk.  That may solve your problem, though you may still need to run ```
sudo update-grub
``` in order for the menu to include windows7.

However, lets see the RESULTS.txt from boot_info_script first.  That may help more.

---

### Post by Amurko on 2010-07-04
I highly, highly, HIGHLY recommend that in the next release of Ubuntu, make 99% of all known Wifi drivers work out of the box!  Even at the expense of other further development!

This can't be emphasized enough!

As long as an internet connection, a basic GUI, and a web browser are working out of the box, any other lingering problem can be substantially easier to solve by Googling for the solution.  If my machine's not working, as long as I've got internet, I can solve all other major issues with research, be it Video Card, sound, usb, performance, etc.

---

### Post by philinux on 2010-07-04
And the output of bootinfoscript is still awaited?

---

### Post by Amurko on 2010-07-04
I reinstalled one more time and it seems to have finally restored GRUB (this time, I reinstalled + reformatted when it was reporting "Missing Operating System) on startup rather than some random garbage characters.  (Nothing much was lost since I just tried reinstalling to no avail yesterday but it apparently has worked this time.)

---

### Post by philinux on 2010-07-04
Nice one. Be sure to check the general help forum sticky.

---

