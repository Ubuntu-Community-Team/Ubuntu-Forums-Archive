---
title: "Won't install on Vista?"
date: 2011-05-23
forum: General Help
---

### Post by Narfboy93 on 2011-05-23
I keep getting a Permission Denied window when trying to install 11.04. I have tried from boot and from within windows. I am running it off of a CD and have UAC turned off. Any ideas?

---

### Post by linuxinstalledfromhdd on 2011-05-23
I suggest a walkthrough:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Narfboy93 on 2011-05-23
For what? That's a to-do list after installing and it's for 10.10. ???

---

### Post by linuxinstalledfromhdd on 2011-05-23
Can you please be more specific what you are trying to do?  What kind of system is this?

---

### Post by dFlyer on 2011-05-23
> **Narfboy93 said:**
> I keep getting a Permission Denied window when trying to install 11.04. I have tried from boot and from within windows. I am running it off of a CD and have UAC turned off. Any ideas?

I'm going to assume your talking about creating a dual boot system. Are you trying to install on a separate drive or on the same HD as windows? Hopefully you have free disc space. IE did you resize windows to free space so you can create a partition to install ubuntu to?

---

### Post by linuxinstalledfromhdd on 2011-05-23
If you wipe the entire hard drive first. Then install Windows 7. And then install Ubuntu from a live disc, doesn't it prompt to provide the user the ability to resize the partition? Won't it do it automatically, without prep?

---

### Post by 3rdalbum on 2011-05-23
Are you booting up the computer from the CD, or using the Windows program that comes on the CD?

If the latter, then try booting the computer from the CD (requires you to go into the BIOS setup and set the boot order so that the CD gets booted first) and installing Ubuntu this way.

---

### Post by Narfboy93 on 2011-05-23
1.) I am trying to install 11.04 and I am running Vista.

2.) I definitely have free space.

3.) I tried both from the boot and the program

4.) On the same hard-drive. I was looking to dual boot it to try it for a while then only Ubuntu. The demo doesn't want to work either, it comes up to a command line screen with no seeming way to get out of.

5.) I have changed the boot process

---

### Post by linuxinstalledfromhdd on 2011-05-23
Your statement on 3 doesn't make sense to me for some reason.

Did you insert the disc in the drive, reboot your computer, and boot from that disc and not the hard drive?

---

### Post by Narfboy93 on 2011-05-23
Yes, I tried booting from the disc(after rebooting and shutting down) and from inside windows

---

### Post by backu on 2011-05-23
> **Narfboy93 said:**
> 1.) I am trying to install 11.04 and I am running Vista.

2.) I definitely have free space.


Free space in windows is not the same as free disk space these guys are talking about. What you need for a proper dual-boot system is Unpartitioned space on the hard drive.. Example: 200GB HD, 100GB is partitioned as NTFS (for Windows), the rest (99.9GB) is UNPartitioned (No Filesystem)

---

### Post by Narfboy93 on 2011-05-23
> **backu said:**
> Free space in windows is not the same as free disk space these guys are talking about. What you need for a proper dual-boot system is Unpartitioned space on the hard drive.. Example: 200GB HD, 100GB is partitioned as NTFS (for Windows), the rest (99.9GB) is UNPartitioned (No Filesystem)


So how would I check/change that? I remember I installed Ubuntu a couple releases ago with no problem on the same laptop

---

### Post by linuxinstalledfromhdd on 2011-05-23
Well if you are saying that you are trying to boot from a 11.04 and it will not boot. Try burning a 10.10 disc of Ubuntu and booting from that. The installer on the desktop within the live environment will allow you to repartition automatically, and create the space needed to install Ubuntu. Don't use Wubi, and try the disc method instead.

---

### Post by Narfboy93 on 2011-05-23
So install 10.10 first THEN upgrade to 11.04?

---

