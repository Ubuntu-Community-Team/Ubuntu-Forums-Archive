---
title: "Boot repair scan problem"
date: 2012-03-02
forum: General Help
---

### Post by sirriffsalot on 2012-03-02
Hello! I have downloaded and made a bootable DVD out of the Ubuntu Secure package, but I never seem to get past the scanning process of the boot repair option... It spends a while where it says that it may take a few minutes, then when it arrives at a few seconds it never gets any further and at some point just stops while the sound coming from the DVD-reader is clearly indicating a lag, as if it cannot get any further... Should the scan take long anyway, like 10 minutes to 15 minutes?

Is this a known problem? Any suggestions on how to fix this or how to sort out a boot selection screen between Ubuntu Studios and Windows Vista? It automatically goes for Vista since I had to skip the boot part in the Ubuntu Studio install process since it did not work out, since I knew this was a relatively easy fix... Thanks for your time and any further time you choose to spend on helping out!!

--> Leo

Edit - now I finally got to the selection stage after the scan, but new problems arrived! 

I was told to do 

sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub-common

in a terminal, which only gave me 

Package grub-common is not installed, so not removed

So... Now what? 

Cheers!

Edit again - Hi again! Instead of trying the CD way I might as well have gone for the terminal way... Described here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Although I installed ubuntu afterwards, I presume the principle is the same - getting the dual boot selection options back.

So I did "sudo fdisk -l" first to see which would be the partition with ubuntu installed

Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   683593812   341796875    7  HPFS/NTFS/exFAT
/dev/sda2       683595774   976769023   146586625    5  Extended
/dev/sda5       683595776   972576767   144490496   83  Linux
/dev/sda6       972578816   976769023     2095104   82  Linux swap / Solaris

I got this, so dev/sda5 is the one I am supposed to put into the

sudo grub-install /dev/XXX

command, is this correct? If so, I received this as a response:

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

So... NOW what?:) Sorry for the rapid changes... Really excited to get things going so:)

Cheers once again!

---

