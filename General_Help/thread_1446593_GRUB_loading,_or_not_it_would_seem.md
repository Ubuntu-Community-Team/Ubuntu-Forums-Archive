---
title: "GRUB loading, or not it would seem"
date: 2010-04-04
forum: General Help
---

### Post by random_excess23 on 2010-04-04
I would really appreciate some help with this.

I have a dual boot PC running Karmic and XP pro. Everything has been chugging along fine for several months but now it will not boot :-(

I attempted to install Adobe Creative Suite under Windows but could not install successfully so I elected to remove the shared components and try again. I was prompted to reboot after uninstalling which I did and since then I have been unable to boot into either Windows or Ubuntu.

The computer seems to get through post and bios fine then prints GRUB loading and promptly restarts.

I can access all drives without problem via a live CD but would like some help repairing my current setup, the idea of reinstalling both OSes from scratch is not really how I planned to spend the bank holiday weekend.

---

### Post by Naitsirhc Hsem on 2010-04-04
boot with a live cd and run the grub-install command on your hard drive, probably /dev/sda1 or /dev/hda1 you can find out in gparted.  I have not done this and you can find out what parameters it takes by typing in grub-install --help
good luck!

---

### Post by random_excess23 on 2010-04-04
I have two drives, output of fdisk:

Disk /dev/sda: 123.5 GB, 123522416640 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6127    49215096    7  HPFS/NTFS
/dev/sda2            6128       15017    71408925    5  Extended
/dev/sda5            6128        6492     2931831   82  Linux swap / Solaris
/dev/sda6            6493        8437    15623181   83  Linux
/dev/sda7            8438       15017    52853818+  83  Linux

Disk /dev/sdb: 323.9 GB, 323928170496 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       39381   316327851    7  HPFS/NTFS

I have two operating systems installed and a separate home partition for Ubuntu. I am concerned that I will not be able to access everything after reinstalling GRUB.

---

### Post by john newbuntu on 2010-04-04
There appears to be a problem with the bootloader.  Follow the instructions in the following post in this order:
1. How to restore windows xp bootloader
2. How to restore ubuntu grub bootloader (You need the liveCD for this)

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by random_excess23 on 2010-04-04
Thanks very much, that was all very simple and painless.

Reinstalled Grub and everything is working fine.

Now I can go out and enjoy the sunshine :-)

---

