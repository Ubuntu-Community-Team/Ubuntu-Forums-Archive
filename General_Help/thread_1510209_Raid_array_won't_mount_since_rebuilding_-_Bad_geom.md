---
title: "Raid array won't mount since rebuilding - Bad geometry"
date: 2010-06-15
forum: General Help
---

### Post by bandad on 2010-06-15
I had run out of space on a 30GB raid1 partition so I rebuilt it as I had three 30GB partitions on a pair of 120GB drives. I stopped the array and used gparted to create a single 120GB partition on one of the disks. I then copied the data from all three partitions on the other drive onto this newly cleared space, before zapping that too. So I now had two drives with identical single partitions, one of which had all my data and lots of space. I used mdadm to create a new array from the two disks, which looked good. It immediately started to resync the data onto the second drive.

However, when I tried to mount the new array this is what I get:


```
bob@zaphod:~$ sudo mount -t ext4 /dev/md0 /media/raid/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

bob@zaphod:~$ dmesg | tail
[ 3441.413156] md: md0 still in use.
[ 3441.459270] md: bind<sdb1>
[ 3441.459618] md: bind<sdc1>
[ 3441.469760] raid1: raid set md0 active with 2 out of 2 mirrors
[ 3441.469841] md0: detected capacity change from 0 to 120031412224
[ 3441.470062]  md0: unknown partition table
[ 3455.259881] EXT4-fs (md0): bad geometry: block count 29304560 exceeds size of device (29304544 blocks)

```

Running fdisk -l gives the following (edited for relevant drives):

```
bob@zaphod:~$ sudo fdisk -l

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45934d2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   fd  Linux RAID autodetect

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44f6c033

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241   fd  Linux RAID autodetect

Disk /dev/md0: 120.0 GB, 120031412224 bytes
2 heads, 4 sectors/track, 29304544 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

I can mount the drives independently and GOOD NEWS the data is there! However, how can I get round this problem and mount the raid array.

ps. running amd64 Lucid

---

### Post by bandad on 2010-06-15
<bump>

No one got any helpful suggestions?

---

### Post by bandad on 2010-06-16
Still value some help here.

I notice that the two devices have identical UUID values. Is that normal? Is it a problem?

```
/dev/sdb1: UUID="d2809c9c-75d5-ad1a-df8d-11793cf1071f" TYPE="linux_raid_member" 
/dev/sdc1: UUID="d2809c9c-75d5-ad1a-df8d-11793cf1071f" TYPE="linux_raid_member" 

```

I have tried removing the mdadm.conf and doing a dpkg-reconfigure mdadm. No change. 
I also tried editing the mdadm.conf to specify the devices as follows:

```
# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=d2809c9c:75d5ad1a:df8d1179:3cf1071f
ARRAY /dev/md0 level=raid1 num-devices=2 devices=/dev/sdb1,/dev/sdc1

```
The array assembles fine but still won't mount.
I urgently need to get at this data. I know I can simply mount the drives separately, but then I am throwing away the redundancy and have no backup. There's a Windows 7 vbox instance on these drives with some expensive software licences that I need to be able to use.

Help!

---

### Post by john newbuntu on 2010-06-16
When you originally used gparted to create a 120GB partition, did you zap out the superblocks on that disk?  Same goes for the second disk.

mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1

Also, in your post, there is no mention of creation of a filesystem on the raid array but just a mount of an array.  I am not sure if you did this or not.  So something like this ought to do it.  Do this after the array is created with "mdadm -v --create...":
```
mkfs.ext3 /dev/md0
```

NOTE: In zeroing the superblocks, you will lose your existing data.  So make a data backup b4 you do this and finally copy back into the array.  I don't know if there is a short cut of keeping your data in your existing disk and then automagically adding the mirror.

Finally check status with "cat /proc/mdstat"
and/or "sudo mdadm --query --detail /dev/md0"

---

### Post by bandad on 2010-06-16
Yes, I did zap the superblocks and used gparted to create new partitions, formatted them ext4, and then copied the data. I did them individually because I was juggling precious data.

I guess I could borrow an external drive to back up onto and then try again with totally clean drives. I didn't have any spare disk space to back up this data.

mdadm query looks like this...

```
bob@zaphod:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jun 14 22:11:44 2010
     Raid Level : raid1
     Array Size : 117218176 (111.79 GiB 120.03 GB)
  Used Dev Size : 117218176 (111.79 GiB 120.03 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jun 16 09:07:20 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : d2809c9c:75d5ad1a:df8d1179:3cf1071f (local to host zaphod)
         Events : 0.20

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1

```

---

### Post by john newbuntu on 2010-06-17
> **bandad said:**
> ... formatted them ext4, and then copied the data. I did them individually because I was juggling precious data.

I am a little bit confused here.  Did you individually format the partitions as ext4 or did you format the /dev/md0 as ext4?  What you need to do is the latter. Do not format the partitions individually when you are setting up raid.  And then once you go through the other routine stuff:
"sudo mount /dev/md0 /media/raid"
should get it up and running manually.
Also, you might be aware that what goes into mdadm.conf is the output of the command:
"mdadm --detail --scan".  Follow this up with running a "sudo dpkg-reconfigure mdadm".

---

### Post by bandad on 2010-06-17
Ok, I can appreciate that the formatting after the assembly may be a good idea. I didn't have that choice, as I needed to preserve the data. AFAIK any attempt to format the raid array now will wipe the data.

So it's back to having to borrow some external drive capacity :(

I'm convinced that there is another solution out there, but it will probably take too long to find it.

---

### Post by Eniac on 2010-07-13
just wanted to say thanks guys.

i installed lucid lynx recently and had never installed raid before that so i was expecting the raid to work out of the box once the fresh install was finished but it didnt and wasn't quite sure where to look.

since im pretty much a beginner i didnt even had a clue of the tools at my disposal.

short story, post #4 of this thread was the missing thing. then i was able to mount and use the raid.

---

