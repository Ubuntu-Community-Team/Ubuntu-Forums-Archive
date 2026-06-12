---
title: "Software raid problem"
date: 2009-08-13
forum: General Help
---

### Post by whaase on 2009-08-13
I had played with a software raid5 with my 4 - 1TB drives with Ubuntu desktop. I decided I want to use server instead (big mistake so far)

My raid is broken, and nothing I do seems to be able to wipe it and let me start over. 

I can delete the partition and create a new one. Once I do that though, it start trying to sync the disks. I don't have a md0 drive to "stop", yet when ever I try to format or recreate the raid it tells me all the devices are busy. So, I can't do anything.. I'm stuck between a rock and hard place :(

I've googled, read, and tried everything I can find and nothing seems to work.

I've searched on here and every thread about it leads to a dead end for me.

Anyone?? please!? :)

---

### Post by ViPeRaY on 2009-08-13
Please post the output of commands below:

cat /proc/mdstat

cat /etc/mdadm/mdadm.conf

sudo fdisk -l

---

### Post by whaase on 2009-08-13
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>

```

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR 

# definitions of existing MD arrays

# This file was auto-generated on Thu, 13 Aug 2009 17:28:21 -0600
# by mkconf $Id$

```

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x314c95a5

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c46a8

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000be5a2

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e41d2

   Device Boot      Start         End      Blocks   Id  System


```


Interesting thing I did find. I typed this:

dmsetup -C info

And got this 

```
Name             Maj Min Stat Open Targ Event  UUID
sil_ajaibjcbfcfa 254   0 L--w    0    1      0 DMRAID-sil_ajaibjcbfcfa

```

The sil is the chipset on the old raid controller I had these drives on. I'm not sure how I can wipe these drives to get them back?

---

### Post by ViPeRaY on 2009-08-13
I am not sure if you have any data on your hard drives already. If you do not then i suggest to you to use mdadm to create the raid. It is the best and reliable way.

I have not used dmsetup before. Also instead of creating raids from hard drives, create them from partitions.

Check this guide for mdadm.
[http://linux-raid.osdl.org/index.php/Linux_Raid](http://linux-raid.osdl.org/index.php/Linux_Raid)

I want to summary the commands for you if you decide to use mdadm for raid. You need to install mdadm first though.

sudo apt-get install mdadm

It is going to ask you setup a mailer. Just chose no configuration.

1- Create partitions on hard drives by using fdisk. You need to do this for every single hard drive. In your case sdb, sdc, sdd, sde.
Example step by step (commands that you need to type):
```

sudo fdisk /dev/sdb
n (for creating new partition)
p (for primary partition)
1 (first partition)
--enter to accept default--
--enter to accept default--
w (to save changes)

```2- Now you need to create the raid. For that type the command below.
This command creates the raid 5 setup by using sdb1, sdc1 and sdd1 as main partitions. sde1 is used for spare if any other hard drive goes down.
```

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1 --spare-devices=1 /dev/sde1

```3- After you create the raid you can see the status of the raid by typing:
```

cat /proc/mdstat

```4- Let the raid finish syncing. You can check the sync status by doing step 3.

5- After the sync is completed. If you want to use ext3 as your file system (recommended), format the raid by using below:
```

mkfs.ext3 /dev/md0

```6- If you restart your computer before doing this step, the raid will be unusable. mdadm should create mdadm.conf file but does not. In this step you need to modify mdadm.conf. Use the command below to open it and add the lines below.

First use the command below to view the details of the raid and copy the UUID. You will paste UUID to mdadm.conf file.

```

sudo mdadm --detail /dev/md0

``````

sudo nano /etc/mdadm/mdadm.conf

```Change the file as below: (dots represents rest of the file. No need to change anything there)
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdc1 /dev/sde1

ARRAY /dev/md0 uuid= PASTE YOUR UUID HERE. LEAVE NO SPACE AFTER EQUAL SIGN
             auto=yes
.....
.....
.....
.....
.....
.....

```7- Finally mount your raid which is /dev/md0 and then torture your raid :)

Hopefully that helps...

NOTE: It is because you have already tried to create raid. I would suggest to you do a complete clean install first and then do these. I am assuming you do not have anything in your OS right now. So it will be more healthy for the OS if you do reinstall first.

---

### Post by whaase on 2009-08-13
Nothing is on the disks, and I do want to create a new raid.

Here is the problem. As soon as I create the fist disk (entire disk), here is the last part of the output

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```

Notice it automatically starts syncing. I can't go any further and it keeps telling me I can't create the raid because the disks are busy

```
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: create aborted

```

And this is a brand new install. But it seemed to have detected the previous raid even though the drives have been formatted already.

---

### Post by ViPeRaY on 2009-08-13
The error you are getting is totally normal. Because you are already created the raid and you are trying to partition the hard drives individually which does not make any sense to Ubuntu.

I dont know how you have created the raid before but you have to remove it first. My suggestion is just wipe out the OS and install it. I mean installing Ubuntu takes 15-20 minutes anyway. You will have a fresh OS to start with.

---

### Post by whaase on 2009-08-13
I just edited my post lol This is a brand new install. When I was installing it detected the raid. It asked if I wanted to use it or not. I told it no.

---

### Post by ViPeRaY on 2009-08-13
Use the command below to remove the raid that has been created before. Maybe it is still there. After the command below restart the machine and try to create partitions in every single hard drive.

```

dmsetup remove_all -f

```

---

### Post by whaase on 2009-08-13
YES! That did it. Thank you!!!!!!! :)

---

### Post by ViPeRaY on 2009-08-13
You are welcome.

---

