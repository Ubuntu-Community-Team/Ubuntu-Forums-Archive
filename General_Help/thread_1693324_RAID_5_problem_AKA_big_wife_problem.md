---
title: "RAID 5 problem AKA big wife problem"
date: 2011-02-22
forum: General Help
---

### Post by troutbum13 on 2011-02-22
I have a raid 5 array, it was working fine in 10.04 except that it would not assemble or mount at start-up. I would have to click system | admin | disk utility and then start the array and then remount fstab. The main purpose of this array was to *safely* store my wife's digital photos. When I wasn't home it was a pain to do all that. So I looked around and found [_this thread_]("http://ubuntuforums.org/showthread.php?t=1468064&highlight=raid") and decided to see if I could get it working. 

first I 
```
sudo mv /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.bak
```

Next I reconfigured mdadm
```
sudo dpkg-reconfigure mdadm
```

I then tried to assemble the array
```
sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 1 drives - not enough to start the array.

```

So I tried restoring the back-up copy that I made of mdadm.conf that did not work, I tried to start the array through the disk-utility and that did not work. I manually edited the mdadm.conf to use device names instead of UUIDs, and then reconfigure mdadm again and that did not work. I am out of ideas.

so here is some info on my setup (pastebin links)

[fdisk -l]("http://pastebin.com/xBFw4r7d")

[mdadm.conf]("http://pastebin.com/bha8HF5F")

[mdadm --assemble --scan --verbose]("http://pastebin.com/yHcK5NTE")

Happy to post anything else that maybe useful. I really appreciate any help, there are several hundred GBs on the array...it will be a bad, bad day if they are gone.

---

### Post by troutbum13 on 2011-02-22
```

```update:
```
$ sudo mdadm --assemble --force --scan /dev/md0
mdadm: forcing event count in /dev/sdb1(1) from 82279 upto 82282
mdadm: clearing FAULTY flag for device 1 in /dev/md0 for /dev/sdb1
mdadm: /dev/md0 has been started with 3 drives (out of 4).
```

```
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[2](S) sda1[0] sdd1[4] sdb1[1](F)
      1465150464 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/2] [U__U]
      bitmap: 10/466 pages [40KB], 512KB chunk

unused devices: <none>

```

This looked promising except for the 3 out 4 bit, but the filesytem was read-only, so I tried again and now I can't even force the array to build

```
~$ sudo mdadm --assemble --force --scan --verbose /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 2
mdadm: added /dev/sdd1 to /dev/md0 as 3
mdadm: added /dev/sda1 to /dev/md0 as 0
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error

```

```
$ sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=01.02 spares=1 name=:Media UUID=8b0de977:bfb31ab8:1b79f16c:74c1e9fb
```

I will keep cracking away at it but I would love some advice

---

### Post by troutbum13 on 2011-02-22
after a series of reboots and trying a live disk I finally got the array to build...no good reason that I could tell. I did not change anything.

When I finally got the photos directory mounted, 10-20% of the photos gave I/O errors and would not display or be copied?? 

The raid file system was also mounted read-only in mtab???

WTF is going on? I am copying those files I can to a different machine before I mess with it any further

---

### Post by tgalati4 on 2011-02-22
What model drives are you using?  If they are "green" drives or consumer drives, then you can't expect a reliable RAID configuration.

It sounds like one of the drives took a major dump and the RAID tried to rebuild itself as much as it could.

Better grab a blanket, it's chilly in the living room.

---

### Post by YesWeCan on 2011-02-22
I think the best thing is not to mess with it at all until you can get some expert help. Backup all the files you can.

I have been scouring the web for the past hour or so to try and find something helpful, but not much luck. Lots of raid 5 disaster stories. I think you are doing well to recover 80% compared to other tales I have read. Perhaps an expert can help you recover more. There are some very capable members here if you can attract their attention.

Good luck.

---

### Post by 1clue on 2011-02-22
type **fdisk -l /dev/sda**, and the same for sdb and the rest.

The partition types of all your RAID partitions should be **fd**.  Boot off the server CD, (or better yet the rescue CD) and use **fdisk** to change the partition type.

If your partitions all share the same UUID then I think they will be automatically be assembled.  I think enough information is stored on each partition to let the kernel determine what RAID type and order each partition had.

I haven't tried the 'green' drives, but I've been using consumer drives for quite awhile.  I just pick good reliable consumer drives with good performance, and they work fine.  I even have them spin down, no problem.

I doubt you had a drive go bad.  You were messing with your array, you either scrambled one of the partitions or it wasn't noticed for the array.

Don't use device number.  It's unreliable with modern kernels.  Plugging in another drive will scramble your numbering and cause your array to fail to mount.  Use UUID.

---

### Post by troutbum13 on 2011-02-23
> **tgalati4 said:**
> What model drives are you using?  If they are "green" drives or consumer drives, then you can't expect a reliable RAID configuration.

It sounds like one of the drives took a major dump and the RAID tried to rebuild itself as much as it could.

Better grab a blanket, it's chilly in the living room.

all WD black drives...seems a strange coincidence that the moment I reconfigure mdadm that a drive craps the bed? I got the array to start degraded.

```
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 01.02
  Creation Time : Sat Aug 14 11:17:48 2010
     Raid Level : raid5
     Array Size : 1465150464 (1397.28 GiB 1500.31 GB)
  Used Dev Size : 976766976 (931.52 GiB 1000.21 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Feb 22 21:57:09 2011
          State : active, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :Media
           UUID : 8b0de977:bfb31ab8:1b79f16c:74c1e9fb
         Events : 84234

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       0        0        2      removed
       4       8       49        3      active sync   /dev/sdd1

       1       8       17        -      faulty spare   /dev/sdb1
       2       8       65        -      spare   /dev/sde1

```

Things are still wonky here is an example of what I mean...

[ATTACH]184205[/ATTACH]

---

### Post by troutbum13 on 2011-02-23
> **1clue said:**
> type **fdisk -l /dev/sda**, and the same for sdb and the rest.

The partition types of all your RAID partitions should be **fd**.  Boot off the server CD, (or better yet the rescue CD) and use **fdisk** to change the partition type.

If your partitions all share the same UUID then I think they will be automatically be assembled.  I think enough information is stored on each partition to let the kernel determine what RAID type and order each partition had.

I haven't tried the 'green' drives, but I've been using consumer drives for quite awhile.  I just pick good reliable consumer drives with good performance, and they work fine.  I even have them spin down, no problem.

I doubt you had a drive go bad.  You were messing with your array, you either scrambled one of the partitions or it wasn't noticed for the array.

Don't use device number.  It's unreliable with modern kernels.  Plugging in another drive will scramble your numbering and cause your array to fail to mount.  Use UUID.

I posted a link to fdisk -l in my first post, all the raid partitions are there. This array has been working for months until today.

As UUID, I tried that and couldn't get it to build the array I switched to device names and at least made a little progress. 


just looked at dmesg and it contains a whole lotta
```
[ 5039.053034] md: md0: requested-resync done.
[ 5100.535572] EXT4-fs (dm-0): warning: maximal mount count reached, running e2fsck is recommended
[ 5100.586240] Buffer I/O error on device dm-0, logical block 0
[ 5100.586248] lost page write due to I/O error on dm-0
[ 5100.586631] EXT4-fs (dm-0): recovery complete
[ 5100.586643] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[ 5100.615580] EXT4-fs (dm-3): warning: maximal mount count reached, running e2fsck is recommended
[ 5100.639793] Buffer I/O error on device dm-3, logical block 0
[ 5100.639795] lost page write due to I/O error on dm-3
[ 5100.642938] EXT4-fs (dm-3): recovery complete
[ 5100.642941] EXT4-fs (dm-3): mounted filesystem with ordered data mode
[ 5100.681369] EXT4-fs (dm-1): warning: maximal mount count reached, running e2fsck is recommended
[ 5100.706466] Buffer I/O error on device dm-1, logical block 0
[ 5100.706475] lost page write due to I/O error on dm-1
[ 5100.709716] EXT4-fs (dm-1): recovery complete
[ 5100.709719] EXT4-fs (dm-1): mounted filesystem with ordered data mode
[ 5100.742711] EXT4-fs (dm-2): warning: maximal mount count reached, running e2fsck is recommended
[ 5100.764832] Buffer I/O error on device dm-2, logical block 0
[ 5100.764841] lost page write due to I/O error on dm-2
[ 5100.772274] EXT4-fs (dm-2): recovery complete
[ 5100.772285] EXT4-fs (dm-2): mounted filesystem with ordered data mode
[ 5100.864235] JBD: Failed to read block at offset 256
[ 5100.864247] JBD: recovery failed
[ 5100.864253] EXT4-fs (dm-4): error loading journal
[ 5107.123161] Buffer I/O error on device dm-1, logical block 6324224
[ 5107.123170] lost page write due to I/O error on dm-1
[ 5107.123206] JBD2: I/O error detected when updating journal superblock for dm-1-8.
[ 5107.145161] Buffer I/O error on device dm-2, logical block 2655233
[ 5107.145169] lost page write due to I/O error on dm-2
[ 5107.145198] Buffer I/O error on device dm-3, logical block 6324224
[ 5107.145205] JBD2: I/O error detected when updating journal superblock for dm-2-8.
[ 5107.145214] lost page write due to I/O error on dm-3
[ 5107.145232] Buffer I/O error on device dm-0, logical block 13139968
[ 5107.145237] lost page write due to I/O error on dm-0
[ 5107.145244] JBD2: I/O error detected when updating journal superblock for dm-3-8.
[ 5107.145256] JBD2: I/O error detected when updating journal superblock for dm-0-8.
[ 5107.145339] Aborting journal on device dm-2-8.
[ 5107.145352] Aborting journal on device dm-1-8.
[ 5107.145393] Aborting journal on device dm-3-8.
[ 5107.145401] Buffer I/O error on device dm-2, logical block 2655233
[ 5107.145406] Aborting journal on device dm-0-8.
[ 5107.145412] lost page write due to I/O error on dm-2
[ 5107.145426] JBD2: I/O error detected when updating journal superblock for dm-2-8.
[ 5107.145434] Buffer I/O error on device dm-1, logical block 6324224
[ 5107.145439] lost page write due to I/O error on dm-1
[ 5107.145453] JBD2: I/O error detected when updating journal superblock for dm-1-8.
[ 5107.145458] Buffer I/O error on device dm-3, logical block 6324224
[ 5107.145463] lost page write due to I/O error on dm-3
[ 5107.145478] JBD2: I/O error detected when updating journal superblock for dm-3-8.
[ 5107.145484] Buffer I/O error on device dm-0, logical block 13139968
[ 5107.145489] lost page write due to I/O error on dm-0
[ 5107.145502] JBD2: I/O error detected when updating journal superblock for dm-0-8.
[ 5109.218706] EXT4-fs error (device dm-1): ext4_journal_start_sb: Detected aborted journal
[ 5109.218719] EXT4-fs (dm-1): Remounting filesystem read-only
[ 5109.257372] EXT4-fs error (device dm-2): ext4_journal_start_sb: Detected aborted journal
[ 5109.257376] EXT4-fs (dm-2): Remounting filesystem read-only
[ 5109.349998] EXT4-fs error (device dm-3): ext4_journal_start_sb: Detected aborted journal
[ 5109.350010] EXT4-fs (dm-3): Remounting filesystem read-only
[ 5112.366117] EXT4-fs error (device dm-0): ext4_journal_start_sb: Detected aborted journal
[ 5112.366130] EXT4-fs (dm-0): Remounting filesystem read-only


```

---

### Post by troutbum13 on 2011-02-23
Need someone to school me on superblocks. It seems like that is the common link between the RAID issues and the EXT4 I/O errors? If the superblocks got tweaked or trashed would that explain the problems I am having?

---

### Post by 1clue on 2011-02-23
I wonder if you have your array assembled properly?  **cat /proc/mdstat** and see if your array is assembled the way you expect.  The problem with using device names is that they change as soon as the hardware changes.

Here are things I can think of that may cause your situation:
[LIST=1]
[*]You don't have the proper partitions added to the array.
[*]You don't have ALL the partitions added to the array that were there to start with.
[*]You have a corrupted partition.
[/LIST]

In the first two you will be running a degraded partition, and I'm not really sure how to fix it other than trying to make sure everything is hooked up right.

The third, you need to boot off of a rescue CD (or some partition that is not your MD partition), dismount the md partition and fsck it manually.

---

### Post by troutbum13 on 2011-02-23
> **1clue said:**
> I wonder if you have your array assembled properly?  **cat /proc/mdstat** and see if your array is assembled the way you expect.  The problem with using device names is that they change as soon as the hardware changes.

Here are things I can think of that may cause your situation:
[LIST=1]
[*]You don't have the proper partitions added to the array.
[*]You don't have ALL the partitions added to the array that were there to start with.
[*]You have a corrupted partition.
[/LIST]

In the first two you will be running a degraded partition, and I'm not really sure how to fix it other than trying to make sure everything is hooked up right.

The third, you need to boot off of a rescue CD (or some partition that is not your MD partition), dismount the md partition and fsck it manually.

```
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sde1[2](S) sdd1[4] sdb1[1](F)
      1465150464 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/2] [U__U]
      bitmap: 10/466 pages [40KB], 512KB chunk

unused devices: <none>

```

shows that sdb1 has failed...fine, but it is RAID5 so I should degrade...but all I get are I/O errors I think the data is still intact, just not sure how to get to it.  Here is one reason why I think that...if you look at the attached pic, it is a screen cap of the image preview the top preview is when I browse the array, but if I try and copy those files I get messed up copies on the usb drive? 

[ATTACH]184212[/ATTACH]

I think the third option is most likely, I think there is a journal or superblock problem with the filesystem. This is all ext4 so e2fsck needs to be done on the assembled array? /dev/md0? right? 

The problem array is not a root partion, my / and home directories are on another partition. So can I just unmount the array and e2fsck...or do I really need to boot to a live session?

Thanks all for help, I have not given up yet.

---

### Post by 1clue on 2011-02-23
You just need to not be using it.

I think a little bit of research is in order here.  I've never had a degraded array.  I don't know if you should fsck first or try to un-degrade (regrade?  upgrade?) the array first.  I'd hate to advise you on the wrong thing.  It's getting really late here so I don't think I have time to mess with it.

Good luck.

---

### Post by troutbum13 on 2011-02-23
e2fsck found errors, but did not fix it

---

### Post by 1clue on 2011-02-23
OK we're beyond my expertise at this point, but my guess is that you've got a corrupt sdb1, either through a disk failure or (more likely IMO) you changing something on it during your messing around.  It seems to me that your array is doing what it's designed to do, protecting a partition when one drive has bad data or bad hardware.

I would say find out how to treat sdb1 as a spare and restore the array onto it.

If it's just corrupted data from your experiments, then the error will be fixed and stay that way.  If it's a real disk error either you won't be able to fix it or you'll fix it and then it will have another error sometime later.

---

### Post by tgalati4 on 2011-02-23
Buffer I/O errors seems to be a bad disk controller (bad cable or bad controller board on the disk drive).  

Have your looked at the SMART parameters?

sudo apt-get install smartmontools
sudo smartctl -a /dev/sdb

Burn a copy of Ultimate Boot CD.  Boot from it and run the WD disk utilities--you can do a short test or long test (both are non-destructive) and get a confirmation on the physical health of the drive.

WD Black drives are decent.  Was there sufficient airflow over the drives? Modern drives tend to run hot.  I bet sdb was in the middle of the stack.

---

### Post by troutbum13 on 2011-02-24
> **tgalati4 said:**
> Buffer I/O errors seems to be a bad disk controller (bad cable or bad controller board on the disk drive).  

Have your looked at the SMART parameters?

sudo apt-get install smartmontools
sudo smartctl -a /dev/sdb

Burn a copy of Ultimate Boot CD.  Boot from it and run the WD disk utilities--you can do a short test or long test (both are non-destructive) and get a confirmation on the physical health of the drive.

WD Black drives are decent.  Was there sufficient airflow over the drives? Modern drives tend to run hot.  I bet sdb was in the middle of the stack.

I will use the ultimate boot CD later, but SMART passes on sdb...
```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

it may be a controller issue, but I don't believe it was a coincidence that right after I dpkg-reconfigure mdadm suddenly I had a major hardware failure??

---

