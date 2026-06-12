---
title: "Lost windows 7 boot after installing Ubuntu 11.10"
date: 2012-02-10
forum: General Help
---

### Post by avi.levi99 on 2012-02-10
I recently installed Ubuntu 11.10 on my desktop.
I originally had Windows 7 installed on it, and I wanted a dual boot.
I wanted to install Ubuntu on a different hard-drive than the one containing the the Windows, 
so I partitioned my computer manually and did not use the "install alongside windows" option.
By doing that, I did have the Ubuntu installed on the different HD, but I lost the windows boot option.
I tried the following to fix it:
  - I used the "fdisk -l" and located the windows partitions. I noticed that the "boot" flag was missing. 
    I then used a partition manager ("GParted" or "partiton magic", I can't recall) to flag it as bootable. That didn't work.
  - I tried using grub2 to add the windows to my boot menu. It was added, but when selecting it, I get an error "invalid signature".

These are my partitions (fdisk output). /dev/sdb1 is my windows installation partition.

I would really appreciate any help I can get.

Thank you.

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007960f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   195311615    97654784   83  Linux
/dev/sda2       195313662   321671167    63178753    5  Extended
/dev/sda5       195313664   292968447    48827392   83  Linux
/dev/sda6       292970496   321671167    14350336   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020b0b

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]**/dev/sdb1   *        2048   973088767   486543360    7  HPFS/NTFS/exFAT**[/COLOR]
/dev/sdb2       973090814  1953523711   490216449    5  Extended
/dev/sdb5       973105245  1953520064   490207410    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe73ab482

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          64   976768064   488384000+   c  W95 FAT32 (LBA)

---

### Post by Mark Phelps on 2012-02-10
My recommendation is as follows:
1) Using the info in the link below, download the Boot-Repair ISO and burn it to CD:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

2) Disconnect the Ubuntu drive from your PC
3) Boot from the Boot-Repair CD and attempt to repair the Win7 boot.
When done, confirm that Win7 can boot from the hard drive
4) Disconnect the Win7 drive and connect the Ubuntu drive. If that drive still boots (which I doubt it will), skip this step.  Using an Ubuntu desktop CD, reinstall GRUB to the Ubuntu drive:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

5) Reconnect the Win7 drive -- but continue to boot from the Ubuntu drive.
6) Boot into Ubuntu, open a terminal, and enter "sudo update-grub" (without the quotes).  This will regenerate the default GRUB config file.

When you reboot, you should get a GRUB menu with selections for Ubuntu and for Win7.

---

### Post by avi.levi99 on 2012-02-19
Sorry for the late reply.
I tried what you suggested and it helped me resolve the issue.
The Boot-Repair disk alone did not suffice. 
I had to use the windows installation as well and "repair startup".
Obviously before I used the boot-repair, I did not even have the option to use the windows installation disc.

I do have a problem with the windows now, I get a blue screen.
But this is a different issue.

Thank you very much for your help.

---

