---
title: "Growing an XFS partition with parted"
date: 2010-04-03
forum: General Help
---

### Post by MakOwner on 2010-04-03
This is a lack of familiarity on my part and I couldn't find this clearly documented anywhere. So, hopefully this will help the next person googling in the middle of the night like me.
Moderators if this is in the wrong place, please move this!


I have a software RAID5 with XFS as the filesystem and have just added two more disks to the array and done all the mdadm functions to add them to the array - google that, it's pretty easy to find.

XFS has the xfs_growfs that you can grow the file system, but you have to resize the underlying partition first, else the output of xfs_growfs simply prints the size information about the partition as it exists. 
No hints whatsoever as to why the filesystem hasn't grown.

parted has the ability to grow a partition - google that and you will quickly find parted doesn't support XFS.  You can't resize an XFS partition.

What you can do is simply delete the existing partition and create a new one.  This is the bit of information that is a bit hard to come by.

example:

parted /dev/md0
print
Model: Unknown (unknown)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  3001GB  3001GB  xfs          primary

rm 1

mkpart 1 0 6001GB

print 
Model: Unknown (unknown)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  6001GB  6001GB  xfs          primary


mount the partition - xfs_growfs works on mounted partitions.

mount /dev/md0p1 /media/md0p1

xfs_growfs /media/md0p1



Once you have the steps, it's amazingly fast - I just spent a long time looking for the confirmation that deleting and redefining the partition wouldn't lose data.

---

### Post by Banderon on 2010-04-03
god bless you. i have been struggling with this SAME EXACT SITUATION for a good day now.  it's as if you felt my pain and decided to post this just when you did.

---

### Post by srs5694 on 2010-04-03
A couple of caveats:

First, be *very very careful* when creating that new partition. If it doesn't begin on *exactly* the same sector as the original partition, there are likely to be problems with using the filesystem, much less growing it. GNU Parted defaults to displaying partition boundaries in non-sector units (KB in the OP's example), which can mask small changes, particularly once the start sector moves into the MB or GB territory. If using GNU Parted, I recommend typing "unit s" to change the display units to sectors. That will at least let you see what's going on with better precision. GNU Parted also makes its changes immediately, which could be dangerous. Better to use fdisk (for MBR) or my [GPT fdisk](http://www.rodsbooks.com/gdisk/) (for GPT), which enable you to abort changes. GParted also permits aborting operations, if you prefer a GUI tool.

Second, deleting and re-creating a GPT partition changes its GUID. (Note that this is different from the UUID of the filesystem it contains.) AFAIK, no Linux tool uses this value, so changing the GUID shouldn't make any difference, but I could be wrong, and some other OS might use this value. I don't know of any way of preserving this value in any libparted-based tool. It can be changed in GPT fdisk, but you'd need to copy the original value to the clipboard or to a file, then issue the command to change the partition's GUID and paste it back. Note that none of this is an issue with MBR disks, since they don't have any sort of unique ID code for individual partitions.

---

### Post by Banderon on 2010-04-04
I definitely second the 'unit s' comment.  Also, if your partition had a name before, the name will be gone.  You'll have to also call 'name [NAME]' to restore it.
 
Other than that, though, this guide is perfect.  Worked perfectly for me, at least.

---

### Post by arriflex on 2010-04-16
This just gives me the willies! There has got to be a better way, deleting a partition and re-aligning a new one to the sector scares me. 

However, I can't find a better way; so I would just say to the community that if XFS is going to continue to be installed as the biggest partition in a standard Mythbuntu install, we need to come up with an easier way for users to upgrade their hard disks. 

I just replaced a 1Tb with a 2Tb and hoped to be able to grow that large XFS partition after cloning the drive over. Now I'm considering just running another partition as a separate storage group because it is so much easier to do!

arri

---

### Post by MakOwner on 2010-04-23
> **srs5694 said:**
> A couple of caveats:

First, be *very very careful* when creating that new partition. If it doesn't begin on *exactly* the same sector as the original partition, there are likely to be problems with using the filesystem, much less growing it. GNU Parted defaults to displaying partition boundaries in non-sector units (KB in the OP's example), which can mask small changes, particularly once the start sector moves into the MB or GB territory. If using GNU Parted, I recommend typing "unit s" to change the display units to sectors. That will at least let you see what's going on with better precision. GNU Parted also makes its changes immediately, which could be dangerous. Better to use fdisk (for MBR) or my [GPT fdisk](http://www.rodsbooks.com/gdisk/) (for GPT), which enable you to abort changes. GParted also permits aborting operations, if you prefer a GUI tool.

Second, deleting and re-creating a GPT partition changes its GUID. (Note that this is different from the UUID of the filesystem it contains.) AFAIK, no Linux tool uses this value, so changing the GUID shouldn't make any difference, but I could be wrong, and some other OS might use this value. I don't know of any way of preserving this value in any libparted-based tool. It can be changed in GPT fdisk, but you'd need to copy the original value to the clipboard or to a file, then issue the command to change the partition's GUID and paste it back. Note that none of this is an issue with MBR disks, since they don't have any sort of unique ID code for individual partitions.


Could you give us an example of using the sector count for manipulating the partition?  I'm about to do this again, and would rather be right and safe than just lucky :)
Is there a package in the respository for your GPT fdisk?

In my case there is no GUI available, the box runs headless without X at all.

---

### Post by srs5694 on 2010-04-23
> **MakOwner said:**
> Could you give us an example of using the sector count for manipulating the partition?  I'm about to do this again, and would rather be right and safe than just lucky

Details vary depending on whether you're using GNU Parted, GParted, fdisk, gdisk, or some other tool. Here's an example with fdisk (done on a USB flash drive):

```

fdisk /dev/sdc

The number of cylinders for this disk is set to 15418.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): u
Changing display/entry units to sectors

Command (m for help): p

Disk /dev/sdc: 16.2 GB, 16166944768 bytes
64 heads, 32 sectors/track, 15418 cylinders, total 31576064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2872a8cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    14745599     7372784   83  Linux

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (32-31576063, default 32): 32
Last sector, +sectors or +size{K,M,G} (32-31576063, default 31576063): 
Using default value 31576063

Command (m for help): p

Disk /dev/sdc: 16.2 GB, 16166944768 bytes
64 heads, 32 sectors/track, 15418 cylinders, total 31576064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2872a8cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    31576063    15788016   83  Linux

Command (m for help): w

```

Things to note:


[list]
[*]I used the 'u' command to change the units to sectors. Linux fdisk defaults to cylinders, which are imprecise enough that they could be misleading under some circumstances.
[*]Before deleting the original partition, I checked its start point and size via the 'p' command.
[*]I was careful to enter the same start sector for the new partition as was used for the original partition.
[*]I verified the new partition's start sector (via the 'p' command and a comparison to the original 'p' command's output) before saving changes (via the 'w' command). The end was, of course, later on the new partition than on the original.
[*]There's currently a move underway to shift from cylinder alignment to 1MB (2048-sector) alignment, since the latter produces improved performance on some RAID configurations and with some new hard disks. If your current partitions aren't aligned in the way that's natural for the utility you use, you might have to jump through some hoops to change the tool's alignment rules. You could use 'c' in fdisk or 'l' on the gdisk experts' menu to do this, for instance.
[/list]


> Is there a package in the respository for your GPT fdisk?

Yes, but I'm not sure for which versions it's valid, and the last I checked it was a bit elderly (version 0.5.1, IIRC; the current version is 0.6.6). It's the gdisk package. You can also download Debian packages for x86, x86-64, and PowerPC from the project's [Sourceforge page.](http://sourceforge.net/projects/gptfdisk/files/)

---

### Post by MakOwner on 2010-04-23
Sorry to keep bugging you, I'm trying to teach myself basic math on the fly, I think ...

In my case, I'm extending an xfs filesystem on a software raid 5 - 
```

root@shuttle:/home/dale# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Mar  5 11:49:29 2010
     Raid Level : raid5
     Array Size : 10255951552 (9780.84 GiB 10502.09 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr 23 16:46:05 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e8db6c04:5af33c7b:0f8e6487:c68eb25a (local to host shuttle)
         Events : 0.81218

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       81        3      active sync   /dev/sdf1
       4       8       17        4      active sync   /dev/sdb1
       5       8      113        5      active sync   /dev/sdh1
       6       8       97        6      active sync   /dev/sdg1
       7       8      129        7      active sync   /dev/sdi1

```

A single partition this large is problematic for fdisk isn't it?
That's why I had used parted with the gpt labels to begin with.

I have already resized the array and am now at the point where I need to extend the file system.
As you can see parted has figured out there are issues with the partition.

```

 parted /dev/md0 print
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing
the old backup)?
Fix/Ignore/Cancel? i                                                      
Warning: Not all of the space available to /dev/md0 appears to be used, you can fix the GPT to use all of the space (an extra 8790815616 blocks) or continue with the current setting? 
Fix/Ignore? i                                                             
Model: Unknown (unknown)
Disk /dev/md0: 10.5TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  6001GB  6001GB  xfs          primary

```

so, if using parted, i would start parted
```

root@shuttle:/home/dale# parted /dev/md0
GNU Parted 1.8.8.1.159-1e0e
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) u                                                                
Unit?  [compact]? s                                                       
(parted) print                                                            
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing
the old backup)?
Fix/Ignore/Cancel? i                                                      
Warning: Not all of the space available to /dev/md0 appears to be used, you can fix the GPT to use all of the space (an extra 8790815616 blocks) or continue with the current setting? 
Fix/Ignore? i                                                             
Model: Unknown (unknown)
Disk /dev/md0: 20511903104s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End           Size          File system  Name     Flags
 1      34s    11721087454s  11721087421s  xfs          primary

```

and then delete the partition and recreate it starting at sector 34 and ending at the max sector. 
Once parted is in "sector" display mode all of the commands will use that unit.  Is that pretty close?

---

### Post by srs5694 on 2010-04-24
The parted "backup GPT table is not at the end of the disk" message indicates that parted has noted the change in the "disk" (RAID array) size. Selecting the "fix" options *should* fix this, but I've not tested parted's behavior in this respect. With GPT fdisk (gdisk), you'd select the 'e' option on the experts' menu to do the same.

> if using parted, i would start parted and then delete the partition and recreate it starting at sector 34 and  ending at the max sector. 
Once parted is in "sector" display mode all of the commands will use  that unit.  Is that pretty close?


Yes, but be sure that parted doesn't change the sector numbers. In fact, I'd recommend using gdisk rather than parted for this, since parted makes its changes immediately, whereas gdisk keeps your changes in memory and commits them to disk only when you tell it to do so. If parted shifts the partition start point in an unexpected way, you may have a hard time recovering it with parted. Also, if you want to preserve the partition's GUID number, you can do so with gdisk (albeit in an awkward way) by cutting-and-pasting the GUID number. (Use 'i' on the main menu to get the data (the "partition unique GUID" value) and then use 'c' on the experts' menu after you've made your changes to paste the original value back in.) I don't know of a way to do this with parted. AFAIK, nothing in Linux relies on GPT partitions' GUID numbers, but I might be unaware of something that does use them.

---

### Post by damorgue on 2011-04-11
Is there really no better way of doing this? I am in a similar situation as well, a grown array with a partition and filesysem that I thought was easily expandable. Has anything changed in the matter lately?

---

### Post by srs5694 on 2011-04-11
> **damorgue said:**
> Is there really no better way of doing this? I am in a similar situation as well, a grown array with a partition and filesysem that I thought was easily expandable. Has anything changed in the matter lately?

I recommend you start a new thread and give the details for *your* configuration. Much of the advice in this thread is specific to the details for the original poster, and we have no way of knowing if the details are applicable to your situation. Be sure to say how your RAID array is configured (hardware vs. Linux software vs. motherboard software/"fake" RAID; and also the RAID level), what partition table type you're using (MBR vs. GPT), what filesystem(s) you're using, what you've tried, and what error messages you've seen in response to your attempts.

---

### Post by damorgue on 2011-04-11
I have found in this forum that if one provides more info, less help is given. If you want, here is my situation:

Four 2TB WD EARS, correctly aligned to their 4K advanced format using parted with a GPT-label. One partition each used in a RAID6 with software-raid. MDADM and CLI used to set it up, chunksize of 256K. A single partition created on the md-device "/dev/md1" (no LVM used, something I regret at this point) and formatted using XFS with default settings. Please ask if there are any questions on this. I then --add another 2TB and --grow to reshape it into a 5-disk RAID6 array. So far so good and everything is working fine and showing up correct. None of this is really relevant to my question though. What is relevant is this:

I have a 6TB /dev/md1 with a 4TB partition on it with xfs. What I need is to expand the partition to use the full 6TB and then the filesystem to use the entire partition. There are no other partitions on the md-device.

Edit: I realise that the bakgroundinfo is relevant if I decide to do the "remove and overwrite with bigger so that the data is still there"-method but I consider that out of the question, seems waaay to sketchy.

---

### Post by srs5694 on 2011-04-11
You still haven't described what's wrong; however, I can guess: When you expanded your array, the backup GPT data in the array didn't move. You can easily fix this with [GPT fdisk (gdisk or sgdisk).](http://www.rodsbooks.com/gdisk/download.html) (Download the version for whatever variety of Ubuntu you're using. Don't use the version in the repositories; it's very out of date.) You can most easily fix this using sgdisk:

```

sudo sgdisk -e /dev/md1

```

You should ensure that /dev/md1 is the correct device first, though. If you like, you can use gdisk instead of sgdisk; gdisk is an interactive text-mode program, vs. the command-line-driven sgdisk. You can use gdisk to view the partition table (with "p"), verify that my hypothesis is correct (with "v"; if I'm right, it'll report that the backup partition data isn't at the end of the disk), and then type "x" followed by "e" to move the data, and then "w" to save your changes.

Once this is done, you should be able to use GParted to resize the partition and filesystem in a single operation, although you'll probably have to do this from an emergency boot CD unless you boot from another disk and can unmount whatever's on /dev/md1.

---

### Post by damorgue on 2011-04-11
I have not described what is wrong because nothing is :) 
I have yet to try anything to expand the partition/filesystem. I was reading up on expanding xfs and thought I should ask first since a lot of people seem to have issues with it, especially xfs. This is why I was wondering if there is a simple way of expanding a partition and then the filesystem.

I am looking for a way of doing this that does not involve remove, overwrite and hope for the best. I am assuming that the last message doesn't apply since that was a fix for a problem you guessed I had. or do you recommend me to do this anyway?

Regarding the last sentence, I happen to have a CD with gparted since a while back, has anything changed with later versions that will affect this operation? Seems fairly complicated to resize from a bootcd since the array will have to be assembled in gparted.

There is no problem unmounting the filesystem, at least not for anything this short. The array is independant and OS is on another disk. This makes the solution where I don't have to use my bootcd more interesting. Isn't there a way I can do this by unmounting, installing something suitable, resize the partition with said program, then resizing the filesystem and finally mount it again?

Thanks

---

### Post by srs5694 on 2011-04-11
If you can unmount the filesystem, you should be able to resize both it and its carrier partition using GParted. I recommend using a fairly recent version because partitioning tools have been undergoing a lot of changes lately, and older ones can sometimes have bugs or limitations that will prove problematic.

As always, backing up before resizing a data partition is wise, although growing a filesystem from its end is usually safer than shrinking one or moving its start point.

---

### Post by damorgue on 2011-04-12
Everything went fine, no help was really needed apparently. I thought I would encounter problems since so many otherrs seem to have had them. Is it that they have been fixed or why did I not have the issues? I have read everything from not possible to loading in extra modules for xfs in order to expand it.

Thank you for your help, perhaps someone might google their way here and find that there really are no issues like so many forums seem to imply.

---

### Post by PaulDriver on 2012-09-09
Lolz, I used to do that in the dirty old DOS days.
(delete, and replace a partation around it's data)
Forgot all about that.  

Anyway, I have a dandy little Linux NAS, 1TB RAID -1 mirrored, 35 watts, it's great, except one of the drives was having issues.

Took a look around the internet, let's see, 1TB for 80 bucks or yeah, 3TB for $130, right on! 

I mean who wouldn't? I got two. Ones a Segate, other is a Western Digital.

I did this on purpose, less likely for both to fail in short order if they are from different batches or even different makes, just gotta make sure the performance and capacity are similar.

I swapped one of the 3TB drives into the NAS, and let it rebuild on it's own, everything synced up just dandy, but dang, there was 2TBs missing.

I'm gonna need to fix that, please let me find a way other then copying the data off, and back on, please?

I was starting to get getting desperate I couldn't figure out how to do it with anything I could find in Linux, and man was I really dreading the idea of copying a that GB of data over the network.  

SMB's cruddytastic 18MBps (NAS has no NFS support) that's like 16 hours of data copying.

Heck no, the re-mirror took less the that, and the NAS was still available.

So, in desperation, I booted to Windows 7 and started looking at what I had access to.  

I have a legit copy of Acronis, but they no longer let you expand a drive for free, imstead they have a $30 partition program they want you to buy.

OK, if it works, I can pay that, lets grab the Trial.

Well it's not, it's a demo, and wouldn't touch anything over 100mb, and I have no idea if it would really work.
(it did identify the Linux RAID partitions)

On a whim, I looked into Windows 7's Disk Manager.  
I read the help on expand to make sure it was going to do what I though, said WTF, to myself, it's really a backup, click, zip, pop, done. 
( I had it EXPAND NOT extend the GPT partition )  

Who'd a thunk it, as down on Windows as I am lately, it was, for the first time in a while, usefull.  In a meaningfull way, ( other then as revenue generator)

With that done, I booted back to Ubuntu, mounted the drive, dang, it was still a gig, but it had all of it's data!

So, I issued the grow_XFS command.  Whirrrr. Whirrrrrrrrrr. Bamf!  

Took a look, and YES, a 3TB RAID-1 XFS partition, with the existing 1TB of data intact, ready to plug back into the NAS and mirror to the other 3TB drive.  

OK, that was fun. What's next? 
I haven't done a pure source Debian based install since what, 98, 97?

Think I'll try doing that on a RasberryPi, gotta be less frustrating then this was (for a couple of hours at least)

:)

P.D.
(shoot, forgot to turn Noscript off, there went all my whites pacing)

---

### Post by wildmanne39 on 2012-09-09
Old thread closed.

---

