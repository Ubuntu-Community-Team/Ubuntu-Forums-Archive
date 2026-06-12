---
title: "Grub question"
date: 2012-02-13
forum: General Help
---

### Post by Milambar on 2012-02-13
I recently took over a new machine housed in a datacenter, with 3 hard disks.

I did an apt-get dist-upgrade, and one of the upgrades is asking me where Grub is installed.

How do I see which of the 3 disks its currently installed on? Note, I don't need to RECOVER, I just need to see which of the 3 disks its currently installed on.

Also note, this is a headless box in a datacenter, so I can't open any form of graphical tool.

Thanks for your help.

---

### Post by linux6994 on 2012-02-13
using df-a at the command prompt will show you the following:

df -a
Filesystem       1K-blocks      Used Available Use% Mounted on
/dev/sda5        145942832  10408620 128227256   8% /
proc                     0         0         0    - /proc
sysfs                    0         0         0    - /sys
none                     0         0         0    - /sys/fs/fuse/connections
none                     0         0         0    - /sys/kernel/debug
none                     0         0         0    - /sys/kernel/security
udev                960168         4    960164   1% /dev
devpts                   0         0         0    - /dev/pts
tmpfs               386972       960    386012   1% /run
none                  5120         0      5120   0% /run/lock
none                967428       560    966868   1% /run/shm
binfmt_misc              0         0         0    - /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0         0         0    - /home/bedroom/.cache/gvfs
/dev/sdb1        976760000 295942720 680817280  31

---

### Post by Milambar on 2012-02-13
Forgive me for sounding like a beginner here, but how does that tell me where grub is installed?

I have /boot on /dev/sda3, which /boot/grub is a subdr, does that mean I need to select /dev/sda as the location to install grub?

---

### Post by ajgreeny on 2012-02-13
I'm not sure if linux6994's answer will definitely help you, as it just shows you how much disk space of each disk is being used, and where the OS you are running at the time is sitting.  In theory grub can be elsewhere and could be on any of the three disks

To see with certainty where your current grub is running from you need to know which disk is first in your boot priority;  running the **boot-info-script** from the information in the link in my signature will help you here

The first paragraph in the RESULTS.txt file it produces will look similar to this 
```
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
```Note I have two disks with 5 linux OSs in total, and therefore have grub on both of the disks;  you will probably only have one entry for grub.

---

### Post by drs305 on 2012-02-13
> **Milambar said:**
> Forgive me for sounding like a beginner here, but how does that tell me where grub is installed?

I have /boot on /dev/sda3, which /boot/grub is a subdr, does that mean I need to select /dev/sda as the location to install grub?

Generally:

If you are using Grub as the default bootloader (i.e. don't have Windows on a second drive) then you want to install Grub to the drive which BIOS boots first. So in your case, install grub to *sda*. Don't designate a partition - merely the drive.

I couldn't be sure if only the one drive was headless or not. If you have Windows on a second drive and the Windows bootloader hasn't been overwritten by Grub, then you would want to install Grub to the Ubuntu drive only and make sure BIOS boots that drive first. This will leave the Windows bootloader intact on the second drive in case Grub fails and you can at least change the BIOS order and boot Windows.

---

### Post by Milambar on 2012-02-13
> **ajgreeny said:**
> I'm not sure if linux6994's answer will definitely help you, as it just shows you how much disk space of each disk is being used, and where the OS you are running at the time is sitting.  In theory grub can be elsewhere and could be on any of the three disks

To see with certainty where your current grub is running from you need to know which disk is first in your boot priority;  running the **boot-info-script** from the information in the link in my signature will help you here

The first paragraph in the RESULTS.txt file it produces will look similar to this 
```
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
```Note I have two disks with 5 linux OSs in total, and therefore have grub on both of the disks;  you will probably only have one entry for grub.

The script worked for me. Perfect, thank you.

---

