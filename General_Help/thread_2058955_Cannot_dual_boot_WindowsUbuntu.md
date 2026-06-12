---
title: "Cannot dual boot Windows/Ubuntu"
date: 2012-09-17
forum: General Help
---

### Post by DrZero99 on 2012-09-17
Hi there! My machine used to be set up as follows: 1 SSD drive with Windows 7 installed and 1 mechanical drive used for data. After I installed Ubuntu 12.04.1 on the mechanical one, it simply wouldnt boot, loading Windows 7 as normal. After having tried boot repair, now the startup boot menu doesnt show Windows any longer, and if I pick Linux it takes forever to load and I have to manually shut it down.

Here is my boot repair log: [http://paste.ubuntu.com/1210328/](http://paste.ubuntu.com/1210328/)


It looks like no data is flawed, but I cant figure how to fix the startup process. Anyone willing to help? Thank you in advance.

---

### Post by beboylips on 2012-09-17
Take a live CD of Ubuntu, run from it. Then run grub-install.

Usually it would look something like this, depending on your drive configuration:

```
sudo grub-install /dev/sda 
```

Note, you have to install Grub on your primary hard drive (Boot order #1). 

To find out which hard drive you should install it on, run 
```

sudo fdisk -l 
```

---

### Post by YannBuntu on 2012-09-17
> **beboylips said:**
> Take a live CD of Ubuntu, run from it. Then run grub-install.

Usually it would look something like this, depending on your drive configuration:

```
sudo grub-install /dev/sda 
```

Note, you have to install Grub on your primary hard drive (Boot order #1). 

To find out which hard drive you should install it on, run 
```

sudo fdisk -l 
```

This won't help, because Boot-Repair has already done it, as you can see at the bottom of the Boot-Info in post#1.


[QUOTE=DrZero99]Here is my boot repair log: [http://paste.ubuntu.com/1210328/](http://paste.ubuntu.com/1210328/)[/QUOTE]

Boot-Repair displayed the following advice in its final window:

```
The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

```

This is a good advice. 

Solution:
1) Boot on your Ubuntu CD, choose "Try Ubuntu"
2) Backup your important documents located in your sdb1 partition onto an external disk (or DVDs)
3) Via Ubuntu, reduce your sdb1 partition from 572G to 570GB. Reduce it from the left-side, so that this will create 2GB of free space at the very beginning of the disk. Create a 2GB EXT4 partition in this free space.
4) Run Boot-Repair  --> Advanced options --> "GRUB location" tab --> tick the "Separate /boot partition: sdb1" option  ---> Apply
5) tell us the new URL that will appear
6) Reboot the PC and tell us what you observe

---

### Post by DrZero99 on 2012-09-17
> **YannBuntu said:**
> This won't help, because Boot-Repair has already done it, as you can see at the bottom of the Boot-Info in post#1.




Boot-Repair displayed the following advice in its final window:

```
The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

```This is a good advice. 

Solution:
1) Boot on your Ubuntu CD, choose "Try Ubuntu"
2) Backup your important documents located in your sdb1 partition onto an external disk (or DVDs)
3) Via Ubuntu, reduce your sdb1 partition from 572G to 570GB. Reduce it from the left-side, so that this will create 2GB of free space at the very beginning of the disk. Create a 2GB EXT4 partition in this free space.
4) Run Boot-Repair  --> Advanced options --> "GRUB location" tab --> tick the "Separate /boot partition: sdb1" option  ---> Apply
5) tell us the new URL that will appear
6) Reboot the PC and tell us what you observe


Actually, Id like to completely uninstall ubuntu along with Grub. How can I perform that, given my current disks configuration?

---

### Post by YannBuntu on 2012-09-17
> **DrZero99 said:**
> Actually, Id like to completely uninstall ubuntu along with Grub. How can I perform that, given my current disks configuration?

Simply use OS-Uninstaller: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1340275988.png[/IMG]

---

### Post by beboylips on 2012-09-17
Or just re-install the Windows MBR using the Windows repair disk. Of course, you would need to format the Ubuntu partition or manually delete Ubuntu files after.

---

### Post by darkomano on 2012-09-18
To uninstall Ubuntu from dual-boot with Win 7:
 
1. Boot from Windows 7 Repair/Installation media (CD/DVD/USB)
Choose repair, command prompt then type
 
**bootsect /nt60 all /mbr **<enter>
 
Reboot.
 
2. Later delete Linux & Swap partitions using Disk Management or any Partition tool.

---

