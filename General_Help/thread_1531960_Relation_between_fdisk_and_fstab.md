---
title: "Relation between fdisk and fstab"
date: 2010-07-15
forum: General Help
---

### Post by mynot on 2010-07-15
Since installing 10.4 I've been having startup problems: I get a message requiring me to press S to mount various disks. 

Something which I've never really understood is: what is the relation between fdisk and fstab?

At present fdisk gives sda1 and sda2 as my Linux partitions, sdb1 and sdb2 as my Windows partitions. fstab has:
/dev/sda1 /media/winboot ntfs
/dev/sda2 /media/windata ntfs
/dev/sdb1 /media/sdb1    ext3
/dev/sdb2 /media/sdb2    ntfs
/dev/sdb5 /media/sdb5    swap
which looks a bit sus to me. 

Am I supposed to make my fstab match fdisk, or does fstab modify the result of fdisk when it boots, or what?
Thanks
Tony

---

### Post by WorMzy on 2010-07-15
fdisk displays the partition tables it can detect on the disks you have in your machine and lists them in the order that the disks are detected at boot time; this is why sda and sdb are not fixed identifiers, and the two can switch. For this reason, it is a better idea to use Universally Unique Identifiers (UUIDs) to identify partitions in your fstab file.

To list your partitions UUIDs, open up a terminal and run ```
sudo blkid -c /dev/null
``` This command will list the information it can find about the partitions in your system, such as current device IDs (sda#/sdb#), UUIDs and labels. The UUID is the best identifier, as it doesn't change (unless you force the partition to generate a new UUID). To get fstab to use UUIDs, you just need to change the "/dev/sdXX" to "UUID=<UUID here>".

Oh, and fstab is just a list of filesystems that you want your system to know about, this includes partitions. If it has an entry in fstab, you can mount a partition automatically at boot time.

---

### Post by mynot on 2010-07-16
Thanks WorMzy. Fixed everything.
Tony

---

