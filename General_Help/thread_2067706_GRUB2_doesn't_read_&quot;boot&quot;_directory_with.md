---
title: "GRUB2 doesn't read &quot;boot&quot; directory with different configuration file (in /boot/grub)"
date: 2012-10-07
forum: General Help
---

### Post by HomoHuman on 2012-10-07
_Excuse me, my English is not good enough._
I get "file not found" message and when use the **ls** command:
grub rescue> **ls /boot**

nothing is displayed.
Other variant of command display:
grub rescue> **ls /**
./ ../ /boot /folder
grub rescue> **ls /folder**
./ ../ readme
And command **set** display:
grub rescue> **set**
prefix=(hd0,msdos2)/boot/grub
root=(hd0,msdos2)

Linux command display:
**ls -l /**
drwxr-xr-x 6 root root       4096 date-time boot
drwxr-xr-x 2 root root       4096 date-time folder
**ls -l /boot**
drwxr-xr-x 3 root root       8192 date-time grub
*other files and directories*

Boot flag was activated on partition ext2.
GRUB installation passed without errors.

---

### Post by HomoHuman on 2012-10-07
Additional information.
I installed GRUB2 to the MBR with help of commands:
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

---

### Post by Bashing-om on 2012-10-07
HomoHuman; Hi ! Welcome to the forum.

Not knowing your system configuration, I am not able to give direct advise.

These links will provide the needed instruction to repair/install grub properly.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
[https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

Post back as/if additional assistance is required.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by HomoHuman on 2012-10-08
My system configuration:
Operational system: Kubuntu 11.10;
&#1057;entral processing unit: Intel Pentium Dual CPU T2390 1.86GHz;
Memory: 2 GB;
Video card: NVIDIA GeForce 8400M GS

My BIOS make it possible to load kubuntu-11.10-desktop-amd64 from a USB flash drive.

GRUB2 don't work on my external hard drive (sdb).

---

### Post by HomoHuman on 2012-10-08
All links exept [http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/) I has tried.
I cannot use "insmod" and other commands because GRUB2 do not find any files and directories in /boot.

---

### Post by HomoHuman on 2012-10-08
Please, answer me why I get:
chroot: failed to run command `/bin/bash': No such file or directory
when enter "sudo chroot /mnt".

---

### Post by efflandt on 2012-10-08
Some computers just have a problem booting from large external drives, but I never figured out why.  For example, my Dell desktop PC from 2010 boots Linux fine at the far end of its 1 TB internal drive (near 900 GB out), boots fine from 160 GB USB drive, but cannot boot from 500 GB external drive (falls to grub rescue prompt).  Even if I boot complete grub on internal drive and go to regular grub prompt (instead of rescue), it can see the root of the external drive and into boot, but not into boot/grub.

The same 500 GB USB drives boot Linux fine on older Dell and Toshiba laptops from 2006, so there is nothing wrong with grub or Ubuntu installation on those drives.

---

### Post by HomoHuman on 2012-10-08
**Best thanks, [efflandt]("http://ubuntuforums.org/member.php?u=937632").**

---

### Post by DusteDdk on 2012-10-09
> **efflandt said:**
> Some computers just have a problem booting from large external drives, 

Yup, creating a 3 GiB partition in the beginning solved this for me as well :)

---

### Post by HomoHuman on 2013-01-11
I installed Linux on external hard disk from live CD/live USB successfully with insignificant errors.
My cfg-files (hand-made       and automatically made) look differently.

---

