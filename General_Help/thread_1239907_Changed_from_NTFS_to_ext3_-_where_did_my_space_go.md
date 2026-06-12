---
title: "Changed from NTFS to ext3 - where did my space go?"
date: 2009-08-14
forum: General Help
---

### Post by Thanh-BKK on 2009-08-14
Hi.

So i got it to work, that partition/volume that didn't want to mount - it mounts fine now.

However somehow it lost a full 6.6 Gigabytes!

The volume has the same size as before, after copying all my data from the backup the number of files and amount of data in those files is identical, too.... but there is some space missing. It states something like "32.2 GB in 5,400 files, 38.8 GB used".

Now what happened to those 6.6 additional Gigabytes? There is a folder named "lost+found" but it is empty (what is it for anyway? Such folder was not there when the volume was NTFS)and the trash is empty, too. 

Appreciate any advice.

Kind regards.....

Thanh

---

### Post by gastly on 2009-08-14
You can use the 'Disk Usage Analyzer' program to scan the disk and see which file's are occupying how much space. 

It could also be that the used space is being incorrectly displayed. Check the space in the terminal and see if it's correct.
```
df -h
```

---

### Post by Thanh-BKK on 2009-08-14
Hi :)

Thank you very much for that. I'll try that as soon as i am back home (now at work).

Kind regards....

Thanh

---

### Post by DaithiF on 2009-08-14
It may be the fact that ext3 reserves 5% of the disk by default for system use.  You can verify by running:
sudo tune2fs -l /dev/yourpartition (e.g. /dev/sda1 -- replace sda1 with your partition)
and look for the 'Reserved block count' line.

---

### Post by DaithiF on 2009-08-14
thats a lower-case 'L' character after tune2fs by the way

---

### Post by Johndo1 on 2009-08-14
Same thing happened to me but with like 40Gib's. I just reinstalled Ubuntu and made the partitions manually. It worked fine and I didn't notice a difference with duel-boot or partitioned from the beginning.

---

### Post by gastly on 2009-08-14
You can also try this...
If it's not a system partition you can backup the stuff in it and manually delete it using **gparted** and then create it again using ext3 as filesystem type :)

---

### Post by Thanh-BKK on 2009-08-14
> **gastly said:**
> You can use the 'Disk Usage Analyzer' program to scan the disk and see which file's are occupying how much space. 

It could also be that the used space is being incorrectly displayed. Check the space in the terminal and see if it's correct.
```
df -h
```

Hello.

Neither Disk Usage Analyzer nor the command "df -h" revealed anything noteworthy, they both showed the space being used as it is supposed to be. but please see my attached screen shot where it is clearly visible that there is now 6.1 GB more used that is actually supposed nto be used (also interesting that the "missing space" amount has gotten smaller!)

I will try other options as below and reply again.

Thanh

---

### Post by Thanh-BKK on 2009-08-14
> **DaithiF said:**
> It may be the fact that ext3 reserves 5% of the disk by default for system use.  You can verify by running:
sudo tune2fs -l /dev/yourpartition (e.g. /dev/sda1 -- replace sda1 with your partition)
and look for the 'Reserved block count' line.

Hi :)

Here is what that gives me:

tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   U-Torrent
Last mounted on:          <not available>
Filesystem UUID:          53c6b848-d5ff-4fd8-a851-7638ae0e14be
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              7634944
Block count:              30523904
Reserved block count:     1526195
Free blocks:              21776461
Free inodes:              7629865
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1016
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Fri Aug 14 10:59:26 2009
Last mount time:          Fri Aug 14 11:22:23 2009
Last write time:          Fri Aug 14 11:22:23 2009
Mount count:              4
Maximum mount count:      21
Last checked:             Fri Aug 14 10:59:26 2009
Check interval:           15552000 (6 months)
Next check after:         Wed Feb 10 10:59:26 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      f651a440-5f82-4162-9093-89e850b7f6df
Journal backup:           inode blocks

Ok so i got this here:

Reserved block count:     1526195

But what exactly does it tell me..? Because i don't know about this :) 

@gastly
Noooo i will never, ever, touch this volume again for any modification.... if you search for topics by me you'll find out that it took me quite some effort to get this thing (said volume) to work again after what i thought was a simple "change of file system". It turned out to become a four-hour adventure which made me come late to work even..... now the thing mounts and i can read and write and even set it on fire if i so desire.... whoa and i thought Vista was bad as in telling me what i am allowed to do on my computer and what not, actually Vista is harmless compared with Ubuntu :) Good thing is that i learned a few more CLI commands in the process. 

Kind regards.....

Thanh

---

### Post by DaithiF on 2009-08-14
It means that the filesystem has reserved 1526195 blocks, each 4096 bytes = ~6gigs for system use.  This is 5% of the size of your disk (120gigs) which as I mentioned earlier is the default for ext3 filesystems.  So this reduces the amount of free space you have on the drive by this amount.

If you want to reduce this, you can... it wouldn't be recommended if you are mounting / on this drive, but if it is an extra drive that you are using for your own files, etc, then its fine.

the command to reduce it is:
sudo tune2fs -m X /dev/yourpartition 
where X is a number 0, 1, 2 3, 4 etc representing the percentage of the drive to reserve

---

### Post by Thanh-BKK on 2009-08-14
Hi :)

Thank you very much for explaining it, i do understand now. If Ubuntu thinks it makes it safer to have 5% reserved in case of a meltdown or something then i happily give those 6 GB away for that purpose, as long as i know where they are :)

Now i came across another annoyance... as i have to shut down my machine every evening i naturally rather quickly come across that "routine file system check". While i certainly appreciate that one i do NOT like it's strange habit of coming at no fixed intervals - it can be as high as 21, but also as low as 3 mounts. And now that includes this large partition with it's many files - which takes quite considerable time! 

This alone makes it somewhat impossible for me to convert my remaining three NTFS partitions to ext3 as well..... the computer would be doing "routine file system checks" for over an hour every few days as those partitions are filled with hundreds of thousands of files (it is a 500 GB HDD which is pure data storage, Ubuntu itself runs on a separate 80 GB HDD which is system-only). 

I know it can be changed with tune2fs as well however the volume has to be unmounted for that and, after the adventure in the morning today, i am simply too chicken for that - if i screw up i am indeed screwed. I am just a mouse pusher........ 

Kind regards.....

Thanh

---

### Post by Slim Odds on 2009-08-14
The 5% reserved space isn't really an Ubuntu thing, it's an ext2, etc. thing.

The 5% is was created back when drives where very small, so it was not a ton of space. However, with newer and much larger drive, it's a huge waste of space.

Also, note that it's only really needed for system partitions. It's definitely not needed for a separate /home partition.

Also, the bootable LiveCD or rescue CD makes the need for this minimal.

I'd reduce the space using tune2fs.  1% should be more than enough for a system partition. 0% for everyone else.

---

