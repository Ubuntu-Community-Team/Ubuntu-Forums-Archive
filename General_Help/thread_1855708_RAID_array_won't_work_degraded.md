---
title: "RAID array won't work degraded"
date: 2011-10-06
forum: General Help
---

### Post by sailingboyLLB on 2011-10-06
I'm getting some hardware and building a NAS system and decided to grab 4  drives, load ubuntu and do RAID 5.  I haven't used raid before and I'm a  little nervous about tying data to a RAID system or even a non-windows  usable format (ext4).  So I decided to do a little test in a virtual  machine.  I followed the instructions here [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)  and successfully installed, booted, and tested some basic file  operations and I was pretty pleased.  I wanted to see how easy/hard it  would be recover from a failure.  So I tested it out by removing each  one of the drives one at a time.

drive 1:
sda1 boot partition
sda3 data partition
sda5 swap partition

drive 2:
sdb1 boot partition
sdb3 data partition
sdb5 swap partition

drive 3:
sdc1 data partition

drive 4:
sdd1 data partition

all 4 data partitions are in RAID 5
the swap and boot partitions are each in their own RAID 1
  The actual drive letter changes when a drive is removed.

Removing drive 1 the system boots degraded without any issue.  If I  shutdown add the drive back and boot, I can re-add it to the array and  then the arrays are fine again.
   
  Removing drive 2 has the same result as removing drive 1
   
  Removing drive 3 the RAID 5 array won’t assemble automatically, and no  amount of mdadm commands I’ve tried will fix it.  I examine the 3  drives in the array and they all look good, record the array device  number, and try to assemble it, in the right order, using assemble.  I  usually get an error saying that one of the devices is busy and doesn’t  have a superblock.  I tried creating a new superblock and it says the  device is not suitable for any style of array.  It hasn’t been mounted  by the OS.  Dmsetup table does not list any devices as active.  The OS  will boot, however.  Cat/proc/mdstat shows the array as inactive, but  lists all 3 devices it needs to run degraded with a (S) next to each of  them, I’m not sure what that means.  Shutting down, putting the drive  back in, and starting up, everything works fine without additional  effort.
   
  Removing drive 4 has the same result as removing drive 3
   
  I tried the usual suspects for help and couldn't find anything specific enough in the forums.  What’s going on here?

---

### Post by maniat1k on 2011-10-06
Can you show me what you did...

if you do this

```
:~ # cat /etc/mdadm.conf
```

what you get?

if you do this

```
 :~ # mdadm --assemble --scan --verbose
```

what do you get?

show me this

```
 ~ # cat /proc/mdstat
```

did you try this?


```
 mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm.conf
``` 
hope I have been helpful

---

### Post by collisionystm on 2011-10-06
The only advice I can add here is ditch that raid 5 and go with raid 10. So much better

---

### Post by sailingboyLLB on 2011-10-06
the mdadm.conf file was automatically created during alternate install.  it is located in /etc/mdadm/mdadm.conf

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
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=a4d43fe8:6e412bd3:e32ab128:1e3ced07 name=ubuntu-RAID:0
ARRAY /dev/md/1 metadata=1.2 UUID=a3ea5219:ca8387da:dcad7ca6:1464c021 name=ubuntu-RAID:1
ARRAY /dev/md/2 metadata=1.2 UUID=9f09ec35:8b34abf7:7e76b9f5:00e996b3 name=ubuntu-RAID:2

# This file was auto-generated on Mon, 03 Oct 2011 07:38:38 -0400
# by mkconf $Id$

the 2nd one run w/sudo returns

sudo mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md/0
mdadm: cannot open device /dev/md/1: Device or resource busy
mdadm: /dev/md/1 has wrong uuid.
mdadm: cannot open device /dev/md/0: Device or resource busy
mdadm: /dev/md/0 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb5: Device or resource busy
mdadm: /dev/sdb5 has wrong uuid.
mdadm: cannot open device /dev/sdb3: Device or resource busy
mdadm: /dev/sdb3 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: looking for devices for /dev/md/1
mdadm: cannot open device /dev/md/1: Device or resource busy
mdadm: /dev/md/1 has wrong uuid.
mdadm: cannot open device /dev/md/0: Device or resource busy
mdadm: /dev/md/0 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb5: Device or resource busy
mdadm: /dev/sdb5 has wrong uuid.
mdadm: cannot open device /dev/sdb3: Device or resource busy
mdadm: /dev/sdb3 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: looking for devices for /dev/md/2
mdadm: cannot open device /dev/md/1: Device or resource busy
mdadm: /dev/md/1 has wrong uuid.
mdadm: cannot open device /dev/md/0: Device or resource busy
mdadm: /dev/md/0 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb5: Device or resource busy
mdadm: /dev/sdb5 has wrong uuid.
mdadm: cannot open device /dev/sdb3: Device or resource busy
mdadm: /dev/sdb3 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.

the 3rd:
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb5[1] sda5[0]
      1046516 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      2928651 blocks super 1.2 [2/2] [UU]
      
md2 : inactive sda3[0](S) sdb3[1](S) sdc1[2](S)
      17200128 blocks super 1.2
       
unused devices: <none>

the 4th when run with sudo says permission denied (i used the /etc/mdadm/mdadm.conf for the last part as i believe it should have been).

the drives that are installed all have the correct output with the mdadm --examine (and shows the super block)

manual assembly does the following:
sudo mdadm --assemble /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc1 missing
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has no superblock - assembly aborted

and the partition is not shown in mount
and not shown in dmsetup table as busy.

the important thing to remember here is that of the 4 drive raid5 array, removing 1 of 2 disks works fine, and removing 1 of the other 2 doesn't work at all.  and obviously it works fine with all of them.

let me know if you have any other insights.

---

### Post by kuchera68 on 2011-10-07
I can't vouch that this will work for a raid 5 solution, but I had problems boot with a simple degraded raid1 data array when one of the disks were pulled from the system. I could not manually assemble the raid with only one drive until I stopped the mdadm device, and then did a new scan. That freed the remaining partition to be re-assembled.

```
sudo mdadm -S /dev/md0
sudo mdadm --assemble --verbose --scan
```My post is here: [http://ubuntuforums.org/showthread.php?t=1855425](http://ubuntuforums.org/showthread.php?t=1855425)

It can't hurt if you are just testing with a virtual machine. After doing this the pulled drive was marked as removed from the /dev/md0 device, I had to re-add it which resulted in a re-sync. But all data was available.

---

### Post by sailingboyLLB on 2011-10-07
that did the trick.  i didn't realize there was a distinction between inactive and stopped...

thanks.

---

