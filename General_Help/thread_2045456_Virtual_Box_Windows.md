---
title: "Virtual Box Windows"
date: 2012-08-21
forum: General Help
---

### Post by 3246251196 on 2012-08-21
How are people finding the use of Windows 7 (or other) on Virtual Box. Ideally, I would like to install Ubuntu onto my entire system and use my licensed version of Windows on a Virtual Box.

1- Is it feasible to use Virtual Box with Windows 7 for gaming needs?
2- Would WINE operate better than VB w/ Win 7 for Direct X?

Has anyone tried anything like this?

---

### Post by NM5TF on 2012-09-11
have you considered using a Dual Boot setup???

you can choose which OS to use at boot, that way you don't sacrifice
any performance of either OS....

having said that, let me say that I'm running Win XP inside Ubuntu
with no apparant problems....I use Oracle Virtual Box with the dynamic
disk allocation enabled so it doesn't hog the disk...

Tommy

---

### Post by greatsirkain on 2012-09-11
I still haven't been able to get windows xp pro to run from virtual box, it tells me the disk isn't a boot disk (even though it is) and it wont boot from a live usb stick of ubuntu or windows. Just got wine, I'll let you know how it goes :)

---

### Post by AndyOpie150 on 2012-09-11
I just recently dual booted an old 2003 SONY VAIO with only 120GB hard disk. No problems what so ever.
I used plop bot manager, and Pendrivelinux's utility for putting the Ubuntu.iso onto the USB in a bootable format.

When in the install menu I was allowed the ability to choose the size of the two partitions with a sliding scale box. I choose to put it smack in the middle, but is not necessary.

When I  power up or reboot I am given the option to boot into Windows or Ubuntu. 
Note: It will auto boot into Ubuntu if you do not select anything in 30 sec. 

This dual boot method allows me to still use many LG Utilitys, ADB, SDK, APK Multi-Tool, QtADB, and many other Android Utility programs for my android phone.
I've been seeing that Wine doesn't enable every Utility program designed for the Windows OS, so right now I'm sticking to the dual boot.

NOTE: Using the USB drive makes it quick and easy to transfer anything from Ubuntu to Windows or vice-a-versa. I just leave it in my computer most all the time.

---

### Post by NM5TF on 2012-09-12
> **greatsirkain said:**
> I still haven't been able to get windows xp pro to run from virtual box, it tells me the disk isn't a boot disk (even though it is) and it wont boot from a live usb stick of ubuntu or windows. Just got wine, I'll let you know how it goes :)

what type disk did you use to load XP???

I used an old Gateway "rescue disk" that I had laying around from 2001....
it installed correctly, but I had to install SP2 & SP3 before I could upgrade from IE6 to IE8 for it to be usefull....  

I followed the step-by-step directions at the following site to install
& configure VB....it works flawlessly as can be seen in the following
screenshot.....

go here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

good luck & let us know how it goes.....

Tommy

---

### Post by greatsirkain on 2012-09-12
its just an xp boot disk, i can boot up with it just not in vb for some reason :(

---

### Post by eylisian on 2012-09-12
Maybe copy the xp iso to disk and then mount the iso loopback style. I've done that with both xp as well as 7 and it seems to work pretty well for me.

Performance mileage varies but I wouldn't want to game via winders and VirtualBox, I'd do what some other posters have mentioned, dual boot. I have to use VirtualBox and win 7 for a Java application and performance is OK. Almost as good as a co-worker w/ win 7 native, but not quite. Fullscreen has been great both with Unity and Openbox for windowing.

Good luck.

---

