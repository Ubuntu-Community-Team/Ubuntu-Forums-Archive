---
title: "File System error on startup"
date: 2010-05-24
forum: General Help
---

### Post by stevebond001 on 2010-05-24
Hi
I installed Lucid as a fresh install with 4 partitions:
sda1 as /
sda2 as /home
sda3 as /Win7 (dual booting)
sda4 as swap

Everything worked fine for a while but now I get an error when booting up stating that there are errors on the /home partition and I can either press f (to fix), s (to skip), i (to ignore) or M (to manually fix).

I have tried pressing f to fix which then allows me to boot up and log in OK (also, everything appears to be there on my home partition).  However, I get the same error message when I reboot.

I have also tried booting into a recovery console, unmounting the partition and running fsck on it.  When I do I get a message about invalid group descriptors (I think - not too sure if that's correct), which I can't seem to get rid of.  It says it's backing them up but I get the same error if I rerun the command.

I have tried running from a live CD and checking the file system (can't do it from a normal boot 'cos the /home partition is mounted) and when I check the file system it comes up with a message saying that the partition is not clean, but doesn't give me an option to fix it.  I don't want to delete and recreate the partition as it's 900GB in size so copying / moving the data off beforehand would be very time consuming and tricky. 

Does anyone have any ideas to help me resolve this?

Thanks very much

---

### Post by oldfred on 2010-05-24
Are these the commands you have run:

Must be unmounted:
Try "e2fsck -f /dev/sda2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda2
if errors:
sudo e2fsck -f -y -v /dev/sda2

---

### Post by stevebond001 on 2010-05-25
Hi
Thanks for the reply.
I have tried your suggestions but have received all kinds of error messages.  So I've run a live CD and copied the output from GParted when I used the option to check and fix the partition (as they are very similar error messages).
Hopefully someone can help me as I'm really stuck

Output as follows:

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Check and repair file system (ext3) on /dev/sda2  00:15:54    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 97787655
end: 1847940884
size: 1750153230 (834.54 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:15:54    ( ERROR )
     	
e2fsck -f -y -v /dev/sda2
     	
e2fsck: Group descriptors look bad... trying backup blocks...
Resize inode not valid. Recreate? yes

Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 56 conflicts with some other fs block.
Relocate? yes

Group 0's block bitmap at 54 conflicts with some other fs block.
Relocate? yes

Group 0's inode bitmap at 55 conflicts with some other fs block.
Relocate? yes

Group 1's inode table at 32824 conflicts with some other fs block.
Relocate? yes

Group 1's block bitmap at 32822 conflicts with some other fs block.
Relocate? yes

Group 1's inode bitmap at 32823 conflicts with some other fs block.
Relocate? yes

Group 3's inode table at 98360 conflicts with some other fs block.
Relocate? yes

Group 3's block bitmap at 98358 conflicts with some other fs block.
Relocate? yes

Group 3's inode bitmap at 98359 conflicts with some other fs block.
Relocate? yes

Group 5's inode table at 163896 conflicts with some other fs block.
Relocate? yes

Group 5's block bitmap at 163894 conflicts with some other fs block.
Relocate? yes

Group 5's inode bitmap at 163895 conflicts with some other fs block.
Relocate? yes

Group 7's inode table at 229432 conflicts with some other fs block.
Relocate? yes

Group 7's block bitmap at 229430 conflicts with some other fs block.
Relocate? yes

Group 7's inode bitmap at 229431 conflicts with some other fs block.
Relocate? yes

Group 9's inode table at 294968 conflicts with some other fs block.
Relocate? yes

Group 9's block bitmap at 294966 conflicts with some other fs block.
Relocate? yes

Group 9's inode bitmap at 294967 conflicts with some other fs block.
Relocate? yes

[COLOR="Red"]***_Additional entries as above removed due to size of output_***[/COLOR]

     	
e2fsck: Group descriptors look bad... trying backup blocks...
Resize inode not valid. Recreate? yes

Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 56 conflicts with some other fs block.
Relocate? yes

Group 0's block bitmap at 54 conflicts with some other fs block.
Relocate? yes

Group 0's inode bitmap at 55 conflicts with some other fs block.
Relocate? yes

Group 1's inode table at 32824 conflicts with some other fs block.
Relocate? yes

Group 1's block bitmap at 32822 conflicts with some other fs block.
Relocate? yes

Group 1's inode bitmap at 32823 conflicts with some other fs block.
Relocate? yes

Group 3's inode table at 98360 conflicts with some other fs block.
Relocate? yes

Group 3's block bitmap at 98358 conflicts with some other fs block.
Relocate? yes

Group 3's inode bitmap at 98359 conflicts with some other fs block.
Relocate? yes

Group 5's inode table at 163896 conflicts with some other fs block.
Relocate? yes

Group 5's block bitmap at 163894 conflicts with some other fs block.
Relocate? yes

Group 5's inode bitmap at 163895 conflicts with some other fs block.
Relocate? yes

Group 7's inode table at 229432 conflicts with some other fs block.
Relocate? yes

Group 7's block bitmap at 229430 conflicts with some other fs block.
Relocate? yes

Group 7's inode bitmap at 229431 conflicts with some other fs block.
Relocate? yes

Group 9's inode table at 294968 conflicts with some other fs block.
Relocate? yes

Group 9's block bitmap at 294966 conflicts with some other fs block.
Relocate? yes

Group 9's inode bitmap at 294967 conflicts with some other fs block.
Relocate? yes

Group 25's inode table at 819256 conflicts with some other fs block.
Relocate? yes

Group 25's block bitmap at 819254 conflicts with some other fs block.
Relocate? yes

Group 25's inode bitmap at 819255 conflicts with some other fs block.
Relocate? yes

Group 27's inode table at 884792 conflicts with some other fs block.
Relocate? yes

Group 27's block bitmap at 884790 conflicts with some other fs block.
Relocate? yes

Group 27's inode bitmap at 884791 conflicts with some other fs block.
Relocate? yes

Group 49's inode table at 1605688 conflicts with some other fs block.
Relocate? yes

Group 49's block bitmap at 1605686 conflicts with some other fs block.
Relocate? yes

Group 49's inode bitmap at 1605687 conflicts with some other fs block.
Relocate? yes

Group 81's inode table at 2654264 conflicts with some other fs block.
Relocate? yes

Group 81's block bitmap at 2654262 conflicts with some other fs block.
Relocate? yes

Group 81's inode bitmap at 2654263 conflicts with some other fs block.
Relocate? yes

Group 125's inode table at 4096056 conflicts with some other fs block.
Relocate? yes

Group 125's block bitmap at 4096054 conflicts with some other fs block.
Relocate? yes

Group 125's inode bitmap at 4096055 conflicts with some other fs block.
Relocate? yes

Group 243's inode table at 7962680 conflicts with some other fs block.
Relocate? yes

Group 243's block bitmap at 7962678 conflicts with some other fs block.
Relocate? yes

Group 243's inode bitmap at 7962679 conflicts with some other fs block.
Relocate? yes

Group 343's inode table at 11239480 conflicts with some other fs block.
Relocate? yes

Group 343's block bitmap at 11239478 conflicts with some other fs block.
Relocate? yes

Group 343's inode bitmap at 11239479 conflicts with some other fs block.
Relocate? yes

Group 625's inode table at 20480056 conflicts with some other fs block.
Relocate? yes

Group 625's block bitmap at 20480054 conflicts with some other fs block.
Relocate? yes

Group 625's inode bitmap at 20480055 conflicts with some other fs block.
Relocate? yes

Group 729's inode table at 23887928 conflicts with some other fs block.
Relocate? yes

Group 729's block bitmap at 23887926 conflicts with some other fs block.
Relocate? yes

Group 729's inode bitmap at 23887927 conflicts with some other fs block.
Relocate? yes

Group 2187's inode table at 71663672 conflicts with some other fs block.
Relocate? yes

Group 2187's block bitmap at 71663670 conflicts with some other fs block.
Relocate? yes

Group 2187's inode bitmap at 71663671 conflicts with some other fs block.
Relocate? yes

Group 2401's inode table at 78676024 conflicts with some other fs block.
Relocate? yes

Group 2401's block bitmap at 78676022 conflicts with some other fs block.
Relocate? yes

Group 2401's inode bitmap at 78676023 conflicts with some other fs block.
Relocate? yes

Group 3125's inode table at 102400056 conflicts with some other fs block.
Relocate? yes

Group 3125's block bitmap at 102400054 conflicts with some other fs block.
Relocate? yes

Group 3125's inode bitmap at 102400055 conflicts with some other fs block.
Relocate? yes

Group 6561's inode table at 214990904 conflicts with some other fs block.
Relocate? yes

Group 6561's block bitmap at 214990902 conflicts with some other fs block.
Relocate? yes

Group 6561's inode bitmap at 214990903 conflicts with some other fs block.
Relocate? yes

Inode 1 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Root inode is not a directory. Clear? yes

Inode 8, i_blocks is 0, should be 262408. Fix? yes

Inode 17 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 33 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 49 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 65 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 81 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 97 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 113 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 129 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 193 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

[COLOR="Red"]***_Additional entries as above removed due to size of output_***[/COLOR]


Inode 8145 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8161 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 8177 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Relocating group 0's block bitmap from 54 to 1022...
Relocating group 0's inode bitmap from 55 to 1023...
Relocating group 0's inode table from 56 to 1024...
Relocating group 1's block bitmap from 32822 to 33790...
Relocating group 1's inode bitmap from 32823 to 33791...
Relocating group 1's inode table from 32824 to 33792...
Relocating group 3's block bitmap from 98358 to 99326...
Relocating group 3's inode bitmap from 98359 to 99327...
Relocating group 3's inode table from 98360 to 99328...
Relocating group 5's block bitmap from 163894 to 164862...
Relocating group 5's inode bitmap from 163895 to 164863...
Relocating group 5's inode table from 163896 to 164864...
Relocating group 7's block bitmap from 229430 to 230398...
Relocating group 7's inode bitmap from 229431 to 230399...
Relocating group 7's inode table from 229432 to 230400...
Relocating group 9's block bitmap from 294966 to 295934...
Relocating group 9's inode bitmap from 294967 to 295935...
Relocating group 9's inode table from 294968 to 295936...
Relocating group 25's block bitmap from 819254 to 820222...
Relocating group 25's inode bitmap from 819255 to 820223...
Relocating group 25's inode table from 819256 to 820224...
Relocating group 27's block bitmap from 884790 to 885758...
Relocating group 27's inode bitmap from 884791 to 885759...
Relocating group 27's inode table from 884792 to 885760...
Relocating group 49's block bitmap from 1605686 to 1606654...
Relocating group 49's inode bitmap from 1605687 to 1606655...
Relocating group 49's inode table from 1605688 to 1606656...
Relocating group 81's block bitmap from 2654262 to 2655230...
Relocating group 81's inode bitmap from 2654263 to 2655231...
Error allocating 512 contiguous block(s) in block group 81 for inode table: Could not allocate block in ext2 filesystem
Relocating group 125's block bitmap from 4096054 to 4097022...
Relocating group 125's inode bitmap from 4096055 to 4097023...
Relocating group 125's inode table from 4096056 to 4097024...
Relocating group 243's block bitmap from 7962678 to 7963646...
Relocating group 243's inode bitmap from 7962679 to 7963647...
Relocating group 243's inode table from 7962680 to 7963648...
Relocating group 343's block bitmap from 11239478 to 11240446...
Relocating group 343's inode bitmap from 11239479 to 11240447...
Relocating group 343's inode table from 11239480 to 11240448...
Relocating group 625's block bitmap from 20480054 to 20481022...
Relocating group 625's inode bitmap from 20480055 to 20481023...
Relocating group 625's inode table from 20480056 to 20481024...
Relocating group 729's block bitmap from 23887926 to 23888894...
Relocating group 729's inode bitmap from 23887927 to 23888895...
Relocating group 729's inode table from 23887928 to 23888896...
Relocating group 2187's block bitmap from 71663670 to 71664638...
Relocating group 2187's inode bitmap from 71663671 to 71664639...
Error allocating 512 contiguous block(s) in block group 2187 for inode table: Could not allocate block in ext2 filesystem
Relocating group 2401's block bitmap from 78676022 to 78676990...
Relocating group 2401's inode bitmap from 78676023 to 78676991...
Error allocating 512 contiguous block(s) in block group 2401 for inode table: Could not allocate block in ext2 filesystem
Relocating group 3125's block bitmap from 102400054 to 102401022...
Relocating group 3125's inode bitmap from 102400055 to 102401023...
Error allocating 512 contiguous block(s) in block group 3125 for inode table: Could not allocate block in ext2 filesystem
Relocating group 6561's block bitmap from 214990902 to 214991870...
Relocating group 6561's inode bitmap from 214990903 to 214991871...
Relocating group 6561's inode table from 214990904 to 214991872...
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: aborted

========================================






Please help!!!!

---

### Post by stevebond001 on 2010-05-25
Anyone please??

---

### Post by stevebond001 on 2010-05-25
Bump

---

### Post by oldfred on 2010-05-25
Did it run to completion? If drive still does not work it sounds like a hardware problem creating problems. Anything beyond e2fsck or testdisk is beyond me.

---

### Post by stevebond001 on 2010-05-26
Yes it did run to completion (I have done this several times now).

Not sure if it is a hardware problem as my other partitions seem fine.  I can still boot into Windows 7 which seems to work fine.

Does anyone else have any suggestions please?

Thanks in advance

---

### Post by dino99 on 2010-05-26
you can install partedmagic on a cd or usb stick and boot with it, then you check again your partitions.

If you have enough free room on your hdd, use clonezilla to duplicate your /home to save your data and reformat the first /home partition.

[http://partedmagic.com/](http://partedmagic.com/)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by stevebond001 on 2010-05-26
dino99
Thanks for the info on PartedMagic.  I'm downloading it now and will try it later on today (I'm scanning the disk with R-Linux at the moment).
Don't think I'll be able to clone the partition as the data is about 300GB in size and I've only got about 150 GB of backup space to house it.  I already have backups of certain data from the partition anyway, but I'm trying to get some specific files back which weren't backed up and can be replaced, but this would take weeks (downloads, etc).  Which program on the PartedMagic disk would be the best one for this purpose? (I'll read the guide as well)

---

### Post by stevebond001 on 2010-05-26
Well I tried the partedmagic disk to no avail.

Clonezilla would not clone the partition as it complained about it being uncleanly unmounted.

I'm running out of options here so I may have to blat the disk and start again!

It's so frustrating 'cos I know the data is still there, I just can't get at it......

If anyone has any other ideas I would love to hear them.

---

### Post by oldfred on 2010-05-26
did you try testdisk?

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
Another Choice:
sleuthkit is in repositories:
[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/).

---

### Post by stevebond001 on 2010-05-27
oldfred
Many thanks for your help.

I have tried both testdisk (which is part of the Partedmagic disk) and sleuthkit but both didn't get me access to my data.
Therefore, I've had no alternative than to blat the disk and start reinstalling again (easy to do but a pain all the same...) I then need to start reassembling my data (the stuff I hadn't backed up)

Thanks everyone for your help, it is much appreciated.

---

