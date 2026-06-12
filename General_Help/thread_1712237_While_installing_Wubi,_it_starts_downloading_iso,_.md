---
title: "While installing Wubi, it starts downloading iso, why?"
date: 2011-03-22
forum: General Help
---

### Post by aisajib on 2011-03-22
I mean, I have the latest version of ISO (Ubuntu Maverick Meerkat) downloaded on my computer and then i) made a startup USB disk using Ubuntu's built-in startup disk creator and ii) created a bootable CD drive with that downloaded ISO.

Then whenever I tried installing it inside Windows*, I notice that the installer (Wubi) begins downloading the entire ISO from the Internet. I tried disconnecting the network but that returns an error and the installation stops.

I remember my good days with installing Ubuntu Karmic Koala using Wubi on my computer. It never started downloading. The problem appears to occur with Ubuntu 10.04, 10.10 and 11.04 (I don't care about Natty yet, though).

I want to know why this happens. Since the entire ISO is here, why would it want to download the entire ISO from the Internet? It's impossible to let it download. Is there any possible solution to this problem?

** The reason I'm trying to install Ubuntu inside windows is that I don't want to mess with Grub. My brother installed Ubuntu on his hard drive in a separate partition and when he uninstalled it for some reason, he couldn't log in to Windows because grub was there and MBR was missing. I remember that night. Hell of a long night!* :mad:

---

### Post by Frogs Hair on 2011-03-22
Wubi .exe sets up windows for Ubuntu and begins the torrent download . When I tried Ubuntu with 9.10 Wubi downloaded loaded the ISO , but I did not have a live cd at that time.

At the time I tried 9.10  Wubi had its own website and it's now the official Windows installer . If Wubi installed Ubuntu directly from the disk at that time I don't know why that has changed . Wubi is only an installer and does not contain any of the ISO files . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by aisajib on 2011-03-22
> **Frogs Hair said:**
> Wubi .exe sets up windows for Ubuntu and begins the torrent download . When I tried Ubuntu with 9.10 Wubi downloaded loaded the ISO , but I did not have a live cd at that time.

At the time I tried 9.10  Wubi had its own website and it's now the official Windows installer . If Wubi installed Ubuntu directly from the disk at that time I don't know why that has changed . Wubi is only an installer and does not contain any of the ISO files . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


I suppose there must be some way to use the already downloaded ISO instead of downloading a new one. I'm just hunting for that way.

---

### Post by Frogs Hair on 2011-03-22
> **aisajib said:**
> I suppose there must be some way to use the already downloaded ISO instead of downloading a new one. I'm just hunting for that way.

You can use the ISO for a traditional dual boot .

---

### Post by Shibblet on 2011-03-22
> **aisajib said:**
> I suppose there must be some way to use the already downloaded ISO instead of downloading a new one. I'm just hunting for that way.

Yes!  Put the ISO in the same directory along with a copy of Wubi.  When you run Wubi, make sure that you choose the correct version of Ubuntu that you are going to install.  i.e. Netbook, or Desktop.  

So, if you have the x64 ISO in the file folder with Wubi, when you run Wubi, choose Ubuntu (Not Ubuntu Netbook).

Wubi "should" (being the operative word), recognize the correct ISO, and run the install very quickly.

Hope that works for you.  It worked great for me in the past.  I am now using a full Ubuntu install on a second drive, where Windows is on another.

---

### Post by aisajib on 2011-03-22
> **Shibblet said:**
> Yes!  Put the ISO in the same directory along with a copy of Wubi.  When you run Wubi, make sure that you choose the correct version of Ubuntu that you are going to install.  i.e. Netbook, or Desktop.  

So, if you have the x64 ISO in the file folder with Wubi, when you run Wubi, choose Ubuntu (Not Ubuntu Netbook).

Wubi "should" (being the operative word), recognize the correct ISO, and run the install very quickly.

Hope that works for you.  It worked great for me in the past.  I am now using a full Ubuntu install on a second drive, where Windows is on another.


It worked perfect! I'm grateful to you very much! Thanks for the help.

 I also like full Ubuntu on a separate hard drive, but I don't prefer it because it messes up my grub and MBR. For example, if I remove Ubuntu later, grub is still there and MBR is missing. Then it's a pain to boot in to Windows.

---

### Post by Shibblet on 2011-03-22
> **aisajib said:**
> I also like full Ubuntu on a separate hard drive, but I don't prefer it because it messes up my grub and MBR. For example, if I remove Ubuntu later, grub is still there and MBR is missing. Then it's a pain to boot in to Windows.

No problem.  Glad to help.  

2nd option for you.  A Windows program called Macrium Reflect Free.  It is a drive imaging program.  [http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

What this will do is make a drive image of your windows drive, along with the "ghosted" boot partition for Windows 7.  The program will allow you to create a recovery CD.  So, if you ever have any issues, you can boot from the Macrium Reflect CD, and restore the Windows image, as well as the boot partition.  This will get your computer up and running to your current image in about 15-20 minutes (depending on your drive speed, processor, etc.)

---

### Post by aisajib on 2011-03-23
Thank you so much. That does really help. :)

---

### Post by jerome1232 on 2011-03-23
This may be off topic but as far as the Bootloader goes I actually just use the Windows bootloader and use EasyBCD to enable it to chainload Grub and boot Ubuntu.

---

### Post by mcduck on 2011-03-23
> **aisajib said:**
> It worked perfect! I'm grateful to you very much! Thanks for the help.

 I also like full Ubuntu on a separate hard drive, but I don't prefer it because it messes up my grub and MBR. For example, if I remove Ubuntu later, grub is still there and MBR is missing. Then it's a pain to boot in to Windows.

It takes about 2 minutes to boot a machine with a Windows CD and reinstall it's bootloader. ;)

..or if you are smart you do that from the Windows recovery menu before removing Ubuntu,a nd you won't even need the Windows CD. :D

(also MBR can't be missing, it's the first 512 bytes of your hard drive. As long as the hard drive is there, so is MBR... The bootloader installed into MBR might of course be missing, but like I said that's really, really quick and easy thing to fix.)

---

### Post by aisajib on 2011-03-23
Would you mind if I ask how to fix without a windows installation disk? :)

---

### Post by Kishlay on 2012-07-26
:popcorn:
Hi guys,


You must remember that Wubi and the .iso file must be in the same folder.Only then you must run the wubi.exe setup.


For this open the ubuntu .iso file with winzip or winrar and then extract wubi.exe in the same folder which has ubuntu .iso file.


If you have any problem then you can reach out to me at [email]kishlaymishra@rocketmail.com[/email]


Enjoy,  :)UBUNTU ROCKS!!!!

---

