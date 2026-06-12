---
title: "having some serious issues after trying to automount"
date: 2010-10-07
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-07
I have the following configuration:

SDA - 300GB
sda1 - NTFS SYSTEM RESERVED (For Win 7)
sda2 - NTFS WIN7OS
sda3 - NTFS 80-DATA 
sda4 - Extended for logical partitions
sda5 - ext3 for linux file system
sda6 - swap space

SDB - 2TB
sdb1 - NTFS SYSTEM RESERVED
sdb2 - NTFS BACKUP2TB

SDC - 2TB
sdc1 - ext4 DATA2TB


Now, The only partitions that DONT have data in them and are just there for system purposes is sda1, sda4 and sdb1.

I ran STORAGE DEVICE MANAGER to configure the automount. I didnt really do much but configure it to automount on boot and named the drive under its label (so sdb2 was named DATA2TB). However i believe the first time I didnt name it so it came up as sdb2 in the media folder.

Now I have an issue, after configuring using STORAGE DEVICE MANAGER, sda3 does not work. it comes up with an error during boot up. Even when I turned off all the configurations for STORAGE DEVICE MANAGER, it still happens. This is the error I get when i try to mount it in Ubuntu:

======================
Unable to mount 80-DATA

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line14 in /etc/fstab is bad
mount: cant find /dev/sda3 in etc/fstab or /etc/mtab
===========================


So what exactly has happened and how can i fix it?

---

### Post by gordintoronto on 2010-10-07
Where did you get "storage device manager"?  Does it have any other name? I don't have anything with that name in my menus, nor in Synaptic.

---

### Post by fuzzylogic25 on 2010-10-07
SYSTEM -> ADMINISTRATION -> STORAGE DEVICE MANAGER

I have Ubuntu 10.04. I installed it using the following command:

sudo apt-get install pysdm


I obtained this method from the following site:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by gordintoronto on 2010-10-08
Sadly, the community docs still include some very old, obsolete information. The site you referred to mentions Dapper, which was quite a few years ago.

---

### Post by fuzzylogic25 on 2010-10-09
ok well here is the main problem, i cannot mount a drive anymore. this is the message i get when i try to click it in the PLACES section:

======================
Unable to mount 80-DATA

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line14 in /etc/fstab is bad
mount: cant find /dev/sda3 in etc/fstab or /etc/mtab
===========================


please help as i need to access this data. thanks!

---

