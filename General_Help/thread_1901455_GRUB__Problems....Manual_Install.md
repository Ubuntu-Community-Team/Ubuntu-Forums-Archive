---
title: "GRUB  Problems....Manual Install?"
date: 2011-12-28
forum: General Help
---

### Post by ka9mot on 2011-12-28
Is it possible to manually install GRUB? I am unable to install it during Ubuntu 11.10 install.

I get the following error:

"Executing' grub-install/dev/sda'"
This is a Fatal Error

---

### Post by ka9mot on 2011-12-28
And now I know why:

root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
root@ubuntu:/# 


Any advice?

---

### Post by oldfred on 2011-12-28
Are you using gpt or custom formated MBR(msdos) so the first partition starts very close to the start of the drive?

Post this if MBR.

```
sudo fdisk -lu
```

And post this if gpt or you do not know:

sudo parted /dev/sda unit s print

---

### Post by TroN-0074 on 2011-12-28
Check out that PDF I am attaching here. It will tell you step by steps how to re install GRUB.
Read it and understand it before you start the procedure Good luck to you.

---

### Post by ka9mot on 2011-12-28
OK, I think this is what you meant Fred:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 203.9 GB, 203928109056 bytes
135 heads, 14 sectors/track, 210739 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc25b7b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          14   398294819   199147403    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000edb76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   547220662   273609307+   7  HPFS/NTFS/exFAT
/dev/sdc2       547221502   625141759    38960129    5  Extended
/dev/sdc5       620951552   625141759     2095104   82  Linux swap / Solaris
/dev/sdc6       547221504   616759295    34768896   83  Linux
/dev/sdc7       616761344   620943359     2091008   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa91da91d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS/exFAT
/dev/sdb2       268414020   312560639    22073310    f  W95 Ext'd (LBA)
/dev/sdb5       268414083   312560639    22073278+   7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

---

### Post by oldfred on 2011-12-28
Your sda looks a little strange and the default for grub is to install to sda. But since your install is in sdc6, I would install the grub2 boot loader to sdc and change BIOS to boot from sdc as the default. 

The sda starts at sector 14, most older systems were set to start at sector 63 as the default with XP and older Ubuntu's. Vista and now newer Ubuntu/gparted systems start at sector 2048 so there is plenty of room for grub's core.img. The heads on sda are not standard either. Is sda a SSD, or flash drive or just an old IDE drive that gets promoted to sda by BIOS?

From LiveCD - see note on which install line to use, but the first is supposed to also work with the newer versions of grub, Also be sure to use the same version liveCD as the install:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc6 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc6 if not correct:
sudo fdisk -l
#confirm that linux is sdc6, that drive did not change from sdc
sudo mount /dev/sdc6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdc

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Once you boot into Ubuntu you may need to run this so it remembers to reinstall grub2's boot loader to sdc and not sda on an update to grub.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by ka9mot on 2011-12-30
OK Got it! I imaged my Windows Stuff to this new drive, re-installed Ubuntu and we are golden.

Thanks for your help!

---

