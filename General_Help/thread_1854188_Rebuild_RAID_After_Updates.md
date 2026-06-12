---
title: "Rebuild RAID After Updates"
date: 2011-10-03
forum: General Help
---

### Post by famulusmercury on 2011-10-03
I just installed the latest updates, including the kernel, for a Debian 6 box and it fails to boot due to an error:

 /dev/sda1: clean, 222/121440 files, 30505/242688 blocks
fsck.ext4: Unable to resolve 'UUID=f8066f1f-5eef-4bf9-a279-c0e52219206a'
fsck died with exit status 8
Press Control-D to continue booting.

When  I check the checkfs log is shows the same as above.  md0 still shows up  in dev. When I check the details of md0 this is what I get:

mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sat May 21 19:16:46 2011
     Raid Level : raid5
  Used Dev Size : 962889664 (918.28 GiB 986.00 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct  1 21:43:38 2011
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 8c85fef5:271f3ef7:a654836d:c65ac4f8
         Events : 0.800787

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

There should be a disk 0 /dev/sdb1 and a total of 4 1TB drives in RAID5 for a total of about 3TB usable.

I ran a hardware test on all drives and they passed. Also, they all show up in fdisk:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af0ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      119875   962889728   fd  Linux raid autodetect
/dev/sdb2          119875      121602    13870081    5  Extended
/dev/sdb5          119875      121602    13870080   82  Linux swap / Solaris

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f0d7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      242688   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              31       12162    97440769    5  Extended
/dev/sda5              31       12162    97440768   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004f3b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      119875   962889728   fd  Linux raid autodetect
/dev/sdc2          119875      121602    13870081    5  Extended
/dev/sdc5          119875      121602    13870080   82  Linux swap / Solaris

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00067c69

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      119875   962889728   fd  Linux raid autodetect
/dev/sde2          119875      121602    13870081    5  Extended
/dev/sde5          119875      121602    13870080   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054d94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      119875   962889728   fd  Linux raid autodetect
/dev/sdd2          119875      121602    13870081    5  Extended
/dev/sdd5          119875      121602    13870080   82  Linux swap / Solaris

I  have scoured the forums online and tried add the UUID to this and that  and have also tried mdadm -A -s md0 to rebuild, but nothing has worked  so far.

The UUID in fstab was different from what shows up in mdadm so I changed the one in fstab to match mdadm.

Then I tried the command 
update-initramfs -u

But still no luck.

---

### Post by famulusmercury on 2011-10-03
Output for command

update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-5-amd64
mdadm: cannot open /dev/md/md0: No such file or directory

---

### Post by famulusmercury on 2011-10-03
I didn't realize that there are two different mdadm.conf files.

/etc/mdadm/mdadm.conf
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
ARRAY /dev/md0 UUID=8c85fef5:271f3ef7:a654836d:c65ac4f8

# This file was auto-generated on Sun, 29 May 2011 13:58:36 -0500
# by mkconf 3.1.4-1+8efb9d1




/etc/mdadm.conf
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=0.90 UUID=8c85fef5:271f3ef7:a654836d:$
   devices=/dev/sdc1,/dev/sdd1,/dev/sde1


So in the second one do I need to change the UUID and add /dev/sdb1?

---

### Post by famulusmercury on 2011-10-03
At the very least, can I mount the degraded array? Isn't RAID 5 supposed to be able to work with one "failure?"

---

### Post by famulusmercury on 2011-10-04
mdadm -E /dev/sd[b-e]1 | grep Event
         Events : 200
         Events : 800787
         Events : 800787
         Events : 800787

---

### Post by famulusmercury on 2011-10-07
I found several sites with various solutions to this problem. After trying a few different methods I pretty much followed this thread.

 [http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/](http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/)

When you get to the command: 
 echo "clean" > /sys/block/md0/md/array_state
 I would get a read/bad command error even logged in as root. I then tried "clear" instead of "clean" and it successfully removed the file. I still had no luck following that tutorial afterwards. So, I decided to:

1. Create a new array md0.
2. Create the config file.
3. update-initramfs -k all -u
4. The above "clean" command (because it was in a auto-read only state)

and like magic, it started rebuilding the array!

...it took a while...

and still no luck. When tried to mount the array it said that it needed to be formatted first. Even worse, the array details showed problems as you can see in the pic. 

I ended up just starting from scratch with a new array with a different name - md1.

Afterwards I found these commands floating around. I'm curious if anyone has tried them?

# mdadm -Ac partitions /dev/mdX -m dev
# mdadm -Ac partitions /dev/md0 -m dev

---

