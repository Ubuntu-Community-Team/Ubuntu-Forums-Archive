---
title: "Urgent help boot"
date: 2012-01-20
forum: General Help
---

### Post by plo on 2012-01-20
I have a boot issue I cannot resolve by my self and I am going away on holiday tomorrow and my girlfriend will not be happy with a nonfunctioning computer for 2 weeks.

Kubuntu 11.10 freshly installed earlier in week (been running Ubuntu 10.04) for a couple of years. All was working well untill last night after a reboot (installed prider drivers for HP). Got stuck at BIOS start up screen.
Reset BIOS but the it refused to boot from hd.
Tried several different things.1
* fsck and e2fsck no errors
* able to boot from CD
* able to mount all partitions and can read file systems
* blkid
   /dev/sda1: UUID="7b7e9f34-2e7c-4cca-bc8c-a55f2b915f08" TYPE="ext3" (extra data disk)
/dev/sdb1: UUID="e47756fc-ca97-41fb-a589-ff7b1a47e44c" TYPE="ext4" (/)
/dev/sdb5: UUID="fa7b0623-1c04-46da-9b44-4eb4627b4109" TYPE="ext4" (/home)
/dev/sdb6: UUID="53d59c61-5f0c-4704-bca1-e544b41bb198" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

* Burned a Boot-Repair CD and boot
 BUT the boot-repair application freezes and systemscans  (the same thing happens when I tried Boot-Repair from a regular Kubuntu Live CD).
Partitions are automatically mounted under /mnt/boot-sav/sdxx and availabel.

I am stuck

/Palle

---

### Post by plo on 2012-01-20
Finally found the issue.

Some how the disks had changed priority in the bios (but I still don't understand why boot-repair failed). Related to my extra data disc being ext2??

---

