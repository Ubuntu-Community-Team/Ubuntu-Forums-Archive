---
title: "Grub Error 17"
date: 2011-10-20
forum: General Help
---

### Post by psuchak on 2011-10-20
I am a total novice at Ubuntu and need some help from the folks here.

I have already scanned the forums to see if I can find a similar issue/resolution but havent found anything that will help.

I have a multi-boot system (windows xp) for some years now, and I occasionally boot into ubuntu to try something.  I cant remember the version of Ubuntu I have (I think it may be version 9.04).

Today I cant boot my computer in windows or in ubuntu.  The error I get says something like Loading Grub Stage 1.5 and then Error No 17 instead of bringing up my grub menu.

I burned a copy of 9.04 live CD, and booted with 9.04 and went into a terminal window and typed
sudo fdisk -l and I get the following:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba92ba92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3442    27647833+   7  HPFS/NTFS
/dev/sda2            3443       12366    71682030    7  HPFS/NTFS
/dev/sda3           12367       12761     3172837+   7  HPFS/NTFS
/dev/sda4           12762       14593    14715540    5  Extended
/dev/sda5           12762       14350    12763611   83  Linux
/dev/sda6           14351       14593     1951866   82  Linux swap / Solaris

I have very limited knowledge of ubuntu and could use some help - the friend I had help me set this up is out of town for a few days and I need my computer.

---

### Post by drs305 on 2011-10-20
I can probably get Windows back for you fairly easily from the LiveCD. You are using Grub legacy and I'm a bit hazy on that one without doing some research.

If you want to get Windows back and don't mind losing Grub for the time being, we can redirect the MBR to point to Windows. If Ubuntu is more important, stop here.

From the LiveCD install lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
You will get some messages saying you need to run the lilo configuration files. Don't. Just run the above two commands and reboot. If you Windows files are intact and the boot flag is pointing to the correct partition (it looks like it is) your Windows bootloader should appear.

---

