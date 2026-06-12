---
title: "no firewire hard drive or usb pen drive"
date: 2006-02-21
forum: General Help
---

### Post by crazyspongebob on 2006-02-21
I have Ubuntu Breezy on my dual MP Athlon with 1.5 gb of ram 3 hard drives (2 WD, 1 IBM), an ALi add-on firewire/usb2 card. I connect my LaCie firewire 40 gig hard drive to my box but is not recognized.  

I have HAL running.

+++++++++++++++++++++
hal       8146  0.0  0.2   5124  3828 ?        Ss   15:28   0:00 /usr/sbin/hald
hal       8151  0.0  0.0   1864   592 ?        S    15:28   0:00 hald-addon-acpi
hal       8304  0.0  0.0   1864   628 ?        S    15:28   0:00 hald-addon-storage
hal       8306  0.0  0.0   1864   752 ?        S    15:28   0:00 hald-addon-storage
root      9894  0.0  0.0   3072   768 pts/0    S+   15:54   0:00 grep hald
++++++++++++++++++++

I also have a usb pendrive.  Though recognized and put under Computer, it is not automounted or even mountable.  The following is the detailed error message when I try to mount.

+++++++++++++++++++++++++
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount
++++++++++++++++++++++++++++++

Any suggestion would be appreciated.

Thanks,
J.T.

---

### Post by wrtrdood on 2006-02-21
My external drives show up on /dev/sr0 or /dev/scd0.  My DVD drive is both USB2 and Firewire and I've used it on both which came up as /dev/sr0 both times.  Try that.

---

### Post by crazyspongebob on 2006-02-21
[QUOTE=wrtrdood]My external drives show up on /dev/sr0 or /dev/scd0.  My DVD drive is both USB2 and Firewire and I've used it on both which came up as /dev/sr0 both times.  Try that.[/QUOTE]
Are /dev/sr0 and /dev/scd0 hardwire into fstab file or being detected automagically by HAL.  I had no problem with the usb when using 5.04.  I don't think the situation was created when I installed my add-on usb/firewire card a few months ago since even my usb1 port does not function either.  I would think that this kind of problem would not appear any more.

Update:  I am able to mount the pendrive using * pmount /dev/sda1* since the drive is recognized when I pull up the Disk Manager.  No firewire though.

Update 2: I have attached a screenshot of Device Manager showing the LaCie firewire drive.

---

