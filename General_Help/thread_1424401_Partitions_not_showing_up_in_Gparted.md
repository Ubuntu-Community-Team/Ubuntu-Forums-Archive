---
title: "Partitions not showing up in Gparted"
date: 2010-03-07
forum: General Help
---

### Post by dakoellis on 2010-03-07
I have what is a weird problem, at least I think it is.  I deleted some files and now my partitions do not show up in Gparted.  Instead, the entire disk shows up as unallocated space.  I am still able to run every partition, one of which is ubuntu and another which is Windows without any other apparent problems.  here is my fdisk -l:
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x851064d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2612    20980858+  83  Linux
/dev/sda2            2613        3135     4200997+  82  Linux swap / Solaris
/dev/sda3   *        3136       16069   103884349+   7  HPFS/NTFS
/dev/sda4           16069      121601   847693822+   f  W95 Ext'd (LBA)
/dev/sda5           16069       18749    21535101    7  HPFS/NTFS
/dev/sda6           18750       31804   104864287+  83  Linux
/dev/sda7           31805       95552   512055778+  83  Linux
/dev/sda8           95553      121601   209238561   83  Linux


```

I figure the problem would be a missing file that needs to be restored, but I have no idea what that might be.  any ideas?

Thanks

---

### Post by dcstar on 2010-03-07
> **dakoellis said:**
> I have what is a weird problem, at least I think it is.  I deleted some files and now my partitions do not show up in Gparted.  Instead, the entire disk shows up as unallocated space.  I am still able to run every partition, one of which is ubuntu and another which is Windows without any other apparent problems.
.........
I figure the problem would be a missing file that needs to be restored, but I have no idea what that might be.  any ideas?


Reinstall the package and any other system files that you deleted.

---

### Post by dakoellis on 2010-03-07
> **dcstar said:**
> Reinstall the package and any other system files that you deleted.

I do not know which files I deleted, probably should have mentioned that.

---

### Post by Pascal11110 on 2010-03-07
This might be a grub problem because it seems that gparted can't read the mbr. I'd run sudo update-grub in Ubuntu. That might fix your problem.

---

### Post by dcstar on 2010-03-08
> **Pascal11110 said:**
> This might be a grub problem because it seems that gparted can't read the mbr. I'd run sudo update-grub in Ubuntu. That might fix your problem.

Gparted use various packages it assumes are still available to work, if someone has deleted some of these items - or critical files that they depend upon - then it will not work properly.

Boot off the Ubuntu Install CD and see if that Partition Manager works correctly, then you will know where the problem is.

---

### Post by dakoellis on 2010-03-08
> **Pascal11110 said:**
> This might be a grub problem because it seems that gparted can't read the mbr. I'd run sudo update-grub in Ubuntu. That might fix your problem.

grub updated with no problems, but did not solve the problem.  I did find that my UUID of the boot drive was wrong for some reason, but fixing that was no help either

---

### Post by dakoellis on 2010-03-08
> **dcstar said:**
> Gparted use various packages it assumes are still available to work, if someone has deleted some of these items - or critical files that they depend upon - then it will not work properly.

Boot off the Ubuntu Install CD and see if that Partition Manager works correctly, then you will know where the problem is.

I tried your suggestion and the drive appears to be just an empty drive. just to be clear, none of my data seems to be lost (I haven't checked all 5-600 gb, but it looks good)

---

### Post by dcstar on 2010-03-08
> **dakoellis said:**
> I tried your suggestion and the drive appears to be just an empty drive. just to be clear, none of my data seems to be lost (I haven't checked all 5-600 gb, but it looks good)

Have you totally powered off the PC (no power cable for 30 seconds!) and then restarted?

---

### Post by dakoellis on 2010-03-08
> **dcstar said:**
> Have you totally powered off the PC (no power cable for 30 seconds!) and then restarted?

tried it, no change

---

### Post by cong06 on 2010-03-08
If this is an option, open up gparted, go to View and select "File Systems Support"

Grab a screenshot and post it here. (or simply use it to install the appropriate software)

---

### Post by dakoellis on 2010-03-08
here's what shows up:

[IMG]http://i871.photobucket.com/albums/ab278/dakoellis/Screenshot.png[/IMG]

---

### Post by dakoellis on 2010-03-08
bump. has anyone seen this?

---

### Post by srs5694 on 2010-03-08
First, try using the text-mode parted tool rather than GParted. I suggest this because parted is simpler; it relies on fewer support libraries, so it'll be easier to debug if it shows the same symptom. If it doesn't show the same problem, then that is at least a clue.

If parted shows this problem, try this command:

```

ldd /sbin/parted

```

This will show you the libraries upon which parted depends. If it reports that it can't find any library, then you'll at least have a name of a file to install, and from that you should be able to track down the appropriate package to install.

If parted doesn't show the problem, you can try the same thing with GParted (the binary program file is /usr/sbin/gpartedbin), but GParted links against many more libraries, most of which are related to its GUI display rather than its disk-handling capabilities.

---

### Post by meierfra. on 2010-03-08
I doubt this has anything to do with files you deleted.  Probably there  is small problem with your partition table. Please post the output of

```
sudo parted /dev/sda print
sudo fdisk -lu /dev/sda
sudo sfdisk -d /dev/sda
```

---

### Post by dakoellis on 2010-03-08
> **meierfra. said:**
> I doubt this has anything to do with files you deleted.  Probably there  is small problem with your partition table. Please post the output of

```
sudo parted /dev/sda print
sudo fdisk -lu /dev/sda
sudo sfdisk -d /dev/sda
```

$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x851064d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    41961779    20980858+  83  Linux
/dev/sda2        41961780    50363774     4200997+  82  Linux swap / Solaris
/dev/sda3   *    50363775   258132473   103884349+   7  HPFS/NTFS
/dev/sda4       258132420  1953520064   847693822+   f  W95 Ext'd (LBA)
/dev/sda5       258132483   301202684    21535101    7  HPFS/NTFS
/dev/sda6       301202685   510931259   104864287+  83  Linux
/dev/sda7       510931323  1535042879   512055778+  83  Linux
/dev/sda8      1535042943  1953520064   209238561   83  Linux
$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 41961717, Id=83
/dev/sda2 : start= 41961780, size=  8401995, Id=82
/dev/sda3 : start= 50363775, size=207768699, Id= 7, bootable
/dev/sda4 : start=258132420, size=1695387645, Id= f
/dev/sda5 : start=258132483, size= 43070202, Id= 7
/dev/sda6 : start=301202685, size=209728575, Id=83
/dev/sda7 : start=510931323, size=1024111557, Id=83
/dev/sda8 : start=1535042943, size=418477122, Id=83

I guess it has something to do with overlapping partitions? would there be any way to fix this without reformatting?

---

### Post by meierfra. on 2010-03-08
```
/dev/sda3 * 50363775 [COLOR="Red"]258132473[/COLOR] 103884349+ 7 HPFS/NTFS
/dev/sda4 [COLOR="Red"]258132420[/COLOR] 1953520064 847693822+ f W95 Ext'd (LBA)
/dev/sda5 [COLOR="Blue"]258132483[/COLOR] 301202684 21535101 7 HPFS/NTFS
```


gparted is complaining since /dev/sda3 and /dev/sda4 overlap.

  You could  move the start point of /dev/sda4 by just a little bit.  But there is supposed to be a 63 sector gap between the start points of /dev/sda4 and the logical partition /dev/sda5.  So gparted will still show the whole drive as unallocated.  But as long as you are not planning to use gparted to partition /dev/sda, this is  a decent option.

You could also move the end point of /dev/sda3 a little bit to the left. But depending  on the exact location of the ntfs filesystem on /dev/sda3, you might have to shrink that filesystem. Since gparted does not recognize /dev/sdc you would have to use command line tools for the resizing. 

Before deciding what to do next, I would like to  determine the exact location of the ntfs filesytem.

```

cd ~/Desktop
sudo dd if=/dev/sda3 of=sda3 count=1
sudo dd if=/dev/sda4 of=sda4 count=64
sudo tar -czvf  dump.tar.gz  sda3 sda4 

```
(Be very careful with the "dd" commands. If they run for more than a couple of seconds, stop the process with "Ctrl+c")

This creates the file dump.tar.gz on your desktop. Attach it to your next post.

---

### Post by dakoellis on 2010-03-08
> **meierfra. said:**
> ```
/dev/sda3 * 50363775 [COLOR="Red"]258132473[/COLOR] 103884349+ 7 HPFS/NTFS
/dev/sda4 [COLOR="Red"]258132420[/COLOR] 1953520064 847693822+ f W95 Ext'd (LBA)
/dev/sda5 [COLOR="Blue"]258132483[/COLOR] 301202684 21535101 7 HPFS/NTFS
```


gparted is complaining since /dev/sda3 and /dev/sda4 overlap.

  You could  move the start point of /dev/sda4 by just a little bit.  But there is supposed to be a 63 sector gap between the start points of /dev/sda4 and the logical partition /dev/sda5.  So gparted will still show the whole drive as unallocated.  But as long as you are not planning to use gparted to partition /dev/sdc, this is  a decent option.

You could also move the end point of /dev/sda3 a little bit to the left. But depending  on the exact location of the ntfs filesystem on /dev/sda3, you might have to shrink that filesystem. Since gparted does not recognize /dev/sdc you would have to use command line tools for the resizing. 

Before deciding what to do next, I would like to  determine the exact location of the ntfs filesytem.

```

cd ~/Desktop
sudo dd if=/dev/sda3 of=sda3 count=1
sudo dd if=/dev/sda4 of=sda4 count=64
sudo tar -czvf  dump.tar.gz  sda3 sda4 

```
(Be very careful with the "dd" commands. If they run for more than a couple of seconds, stop the process with "Ctrl+c")

This creates the file dump.tar.gz on your desktop. Attach it to your next post.


before I run the commands, I want to be completely sure of what they do.  does it copy the first block of sda3 and the first 64 blocks of sda4 into isos, or some other files?

also, what does /dev/sdc have to do with anything?

---

### Post by dcstar on 2010-03-08
> **dakoellis said:**
> before I run the commands, I want to be completely sure of what they do.  does it copy the first block of sda3 and the first 64 blocks of sda4 into isos, or some other files?

The dd just copies the data into plain old files on your desktop with those names.

Nothing to worry about.

---

### Post by dakoellis on 2010-03-08
here are the 2 files, I'm still confused about meierfra's mention of /dev/sdc.  what does that have to do with anything?

---

### Post by meierfra. on 2010-03-08
> does it copy the first block of sda3 and the first 64 blocks of sda4 into isos, or some other files?
It copies the first sector of /dev/sda3 to the file sda3, and the first 64 sector of /dev/sda4 to the file sda4.  The last command just creates a "zip" file from sda3 and sda4.

"dd", if used wrongly, can be dangerous. For example if you would leave out the "count=1", "dd"  would try to to copy all of /dev/sda3 to the file sda3.

> meierfra's mention of /dev/sdc. 

Typo. Was supposed to be "/dev/sda".

I'll have a look at the two files now.

---

### Post by meierfra. on 2010-03-09
The ntfs filesystem does occupy the whole partition.  So  the first sector of /dev/sda4 might get  overwritten by a file in Windows and you won't be able to access  your logical partitions any more.

I'm not sure yet  how one should fix this. But I'll do some testing and let you know.

---

### Post by dakoellis on 2010-03-09
> **meierfra. said:**
> The ntfs filesystem does occupy the whole partition.  So  the first sector of /dev/sda4 might get  overwritten by a file in Windows and you won't be able to access  your logical partitions any more.

I'm not sure yet  how one should fix this. But I'll do some testing and let you know.

Does that mean I should stay away from saving files in windows, or using it? its not much of a problem because I only use it for occasional gaming

---

### Post by meierfra. on 2010-03-09
> Does that mean I should stay away from saving files in windows,

It's  unlikely that Windows will write any files so far at the end of the partition. So I don't think there is any immediate danger. 
Anyway, I found the fix.


> But there is supposed to be a 63 sector gap between the start points of /dev/sda4 and the logical partition /dev/sda5. So gparted will still show the whole drive as unallocated.
Actually gparted does not complain if the gap is less than 63 sector. (The testing I had done earlier was flawed)

So I recommend to use sfdisk to move the start point of /dev/sda4:
Download the attached file NewPT.txt to your Desktop

```

cd ~/Desktop
sudo sfdisk --force --no-reread  -O  OldPT.txt /dev/sda < NewPT.txt

```

Save the file OldPT.txt, which should be on your desktop, to some place outside  your  hard drive (flash drive, online storage,..).  In case something goes wrong you will be able to use OldPT.txt to restore your original partition table.
Reboot.  Gparted should now  show all your partitions again.

---

### Post by meierfra. on 2010-03-09
FYI: This is the content of NewPT.txt:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        63, size=  41961717, Id=83
/dev/sda2 : start=  41961780, size=   8401995, Id=82
/dev/sda3 : start=  50363775, size= 207768699, Id= 7, bootable
/dev/sda4 : start= 258132[COLOR="Red"]480[/COLOR], size=1695387[COLOR="Red"]585[/COLOR], Id= f
/dev/sda5 : start= 258132483, size=  43070202, Id= 7
/dev/sda6 : start= 301202685, size= 209728575, Id=83
/dev/sda7 : start= 510931323, size=1024111557, Id=83
/dev/sda8 : start=1535042943, size= 418477122, Id=83
```

So its the same as the output of "sfdisk -d /dev/sda". Only I increase the start point of /dev/sda4 by 60 and decreased the size by 60.

You might look at NewPT.txt. But do not change anything. sfdisk is very picky. Even an extra space at the  end of a line will cause an error.

---

### Post by dakoellis on 2010-03-09
I followed your suggestion, but it did not work.  I am not sure if this was expected, but OldPT.txt is a binary file, and the command produced errors:

```
$ sudo sfdisk --force --no-reread  -O  OldPT.txt /dev/sda < NewPT.txt

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 510931320 does not have an msdos signature
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   2611    2612-  20980858+  83  Linux
/dev/sda2       2612    3134     523    4200997+  82  Linux swap / Solaris
/dev/sda3   *   3135   16068-  12934- 103884349+   7  HPFS/NTFS
/dev/sda4      16068+ 121600  105533- 847693792+   f  W95 Ext'd (LBA)
/dev/sda5      16068+  18748    2681-  21535101    7  HPFS/NTFS
/dev/sda6      18749   31803   13055  104864287+  83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  41961779   41961717  83  Linux
/dev/sda2      41961780  50363774    8401995  82  Linux swap / Solaris
/dev/sda3   *  50363775 258132473  207768699   7  HPFS/NTFS
/dev/sda4     258132480 1953520064 1695387585   f  W95 Ext'd (LBA)
/dev/sda5     258132483 301202684   43070202   7  HPFS/NTFS
/dev/sda6     301202686 510931259  209728574  83  Linux
/dev/sda7     510931323 1535042879 1024111557  83  Linux
/dev/sda8     1535042943 1953520064  418477122  83  Linux
Warning: partition 3 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```any other ideas?

edit: I also just noticed that all my partitions will no longer mount.  when I try to mount them using mount -a, I get "special device UUID=*blah* does not exist."  the partitions that are not mounting are sda4 and sda7.

```

$ sudo fdisk -l
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: invalid flag 0xb5c6 of partition table 7 will be corrected by w(rite)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x851064d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2612    20980858+  83  Linux
/dev/sda2            2613        3135     4200997+  82  Linux swap / Solaris
/dev/sda3   *        3136       16069   103884349+   7  HPFS/NTFS
/dev/sda4           16069      121601   847693792+   f  W95 Ext'd (LBA)
/dev/sda5           16069       18749    21535101    7  HPFS/NTFS
/dev/sda6           18750       31804   104864287+  83  Linux
/dev/sda7   ?      157984      380096  1784120675   b5  Unknown

```

sorry if this does not help, just thought I would put as much relevant information as possible.

---

### Post by meierfra. on 2010-03-09
> but OldPT.txt is a binary file,

Thats normal. It does not only contain the data for the partition table, but also a backup of everything which was overwritten on the hard drive when the new partition table was written. 


> and the command produced errors:
Most of the messages are normal except for:

   sfdisk: ERROR: sector 510931320 does not have an msdos signature

That message makes no sense to me, since I don't see a reason why that sector would have msdos signature.

But the real problem is this:


> dev/sda6     301202686

This used to be

> /dev/sda6 301202685

and makes not sense at all, since NewPT.txt says:

> dev/sda6 : start=301202685 



Lets see what happens if you correct just that error in the partition table:

```
echo 301202685,209728575 |sudo sfdisk -N6 -f -uS  /dev/sda 
```

---

### Post by dakoellis on 2010-03-09
```
$ echo 301202685,209728575 |sudo sfdisk -N6 -f -uS  /dev/sda
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 510931320 does not have an msdos signature
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  41961779   41961717  83  Linux
/dev/sda2      41961780  50363774    8401995  82  Linux swap / Solaris
/dev/sda3   *  50363775 258132473  207768699   7  HPFS/NTFS
/dev/sda4     258132480 1953520064 1695387585   f  W95 Ext'd (LBA)
/dev/sda5     258132483 301202684   43070202   7  HPFS/NTFS
/dev/sda6     301202685 510931259  209728575  83  Linux
Warning: bad partition start (earliest 301202686)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  41961779   41961717  83  Linux
/dev/sda2      41961780  50363774    8401995  82  Linux swap / Solaris
/dev/sda3   *  50363775 258132473  207768699   7  HPFS/NTFS
/dev/sda4     258132480 1953520064 1695387585   f  W95 Ext'd (LBA)
/dev/sda5     258132483 301202684   43070202   7  HPFS/NTFS
/dev/sda6     301202686 510931259  209728574  83  Linux
Warning: partition 3 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

after running the command you gave me, I am now not able to mount anything other than the 2 ntfs partitions and my root partition.  the 3 other ext3 partitions' UUIDs do not exist, and apparently /dev/sda7 is empty:

```
$ sudo fdisk -l
omitting empty partition (7)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x851064d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2612    20980858+  83  Linux
/dev/sda2            2613        3135     4200997+  82  Linux swap / Solaris
/dev/sda3   *        3136       16069   103884349+   7  HPFS/NTFS
/dev/sda4           16069      121601   847693792+   f  W95 Ext'd (LBA)
/dev/sda5           16069       18749    21535101    7  HPFS/NTFS
/dev/sda6           18750       31804   104864287   83  Linux

```

if there is no more ideas, I would just copy the information to another hard drive if i can go back to the original PT

---

### Post by meierfra. on 2010-03-09
Your original partition table had more problems than I had realized.  sfdisk  tried to fix those problems, but made it worse.

> if i can go back to the original PT 

yes, that does seems to be the best move:

Assuming that OldPT.txt is still on the Desktop:
```

cd ~/Desktop
sudo sfdisk --force  --no-reread -I OldPT.txt /dev/sda 
```

---

### Post by dakoellis on 2010-03-09
it doesn't seem to be working:

```

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

```

still i thought id give a restart a try but it did not help.  I guess I could try using a different drive to boot but would that work?

I just tried to list the table in parted and it reported I have a recursive partition

---

### Post by meierfra. on 2010-03-09
> BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe( 8 ), kpartx( 8 )  or reboot your system now,
before using mkfs
That's normal and can be ignored

What is the current status? What partitions are you able to mount? Could you post the output of 

```
sudo parted /dev/sda print
sudo fdisk -lu /dev/sda
sudo sfdisk -d /dev/sda
sudo sfdisk -xluS /dev/sda
```

---

### Post by dakoellis on 2010-03-09
> **meierfra. said:**
> That's normal and can be ignored

What is the current status? What partitions are you able to mount? Could you post the output of 

```
sudo parted /dev/sda print
sudo fdisk -lu /dev/sda
sudo sfdisk -d /dev/sda
sudo sfdisk -xluS /dev/sda
```

heres the output from those commands: 

```

$ sudo parted /dev/sda print
Error: Invalid partition table - recursive partition on /dev/sda.         
Ignore/Cancel? i                                                          
Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ext3
 2      21.5GB  25.8GB  4302MB  primary   linux-swap(v1)
 3      25.8GB  132GB   106GB   primary   ntfs            boot
 4      132GB   1000GB  868GB   extended                  lba
 5      132GB   154GB   22.1GB  logical   ntfs

$ sudo fdisk -lu /dev/sda
omitting empty partition (7)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x851064d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    41961779    20980858+  83  Linux
/dev/sda2        41961780    50363774     4200997+  82  Linux swap / Solaris
/dev/sda3   *    50363775   258132473   103884349+   7  HPFS/NTFS
/dev/sda4       258132480  1953520064   847693792+   f  W95 Ext'd (LBA)
/dev/sda5       258132483   301202684    21535101    7  HPFS/NTFS
/dev/sda6       301202685   510931259   104864287+  83  Linux
$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 41961717, Id=83
/dev/sda2 : start= 41961780, size=  8401995, Id=82
/dev/sda3 : start= 50363775, size=207768699, Id= 7, bootable
/dev/sda4 : start=258132480, size=1695387585, Id= f
/dev/sda5 : start=258132483, size= 43070202, Id= 7
/dev/sda6 : start=301202685, size=209728575, Id=83
$ sudo sfdisk -xluS /dev/sda

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  41961779   41961717  83  Linux
/dev/sda2      41961780  50363774    8401995  82  Linux swap / Solaris
/dev/sda3   *  50363775 258132473  207768699   7  HPFS/NTFS
/dev/sda4     258132480 1953520064 1695387585   f  W95 Ext'd (LBA)

/dev/sda5     258132483 301202684   43070202   7  HPFS/NTFS
    -         301202685 1953520064 1652317380   5  Extended
    -         258132480 258132479          0   0  Empty
    -         258132480 258132479          0   0  Empty

/dev/sda6     301202685 510931259  209728575  83  Linux
    -         510931320 1535042939 1024111620   5  Extended
    -         301202685 301202684          0   0  Empty
    -         301202685 301202684          0   0  Empty

    -         510931320 510931319          0   0  Empty
    -         510931320 510931319          0   0  Empty
    -         510931320 510931319          0   0  Empty
    -         510931320 510931319          0   0  Empty

```

I am currently able to mount sda1, sda3 to what I remember.  from my original partitions, I should have 3 ext3 partitions and one NTFS remaining to be mounted. however I can only mount the remaining NTFS(which normally wouldn't be mounted) and one of the remaining ext3 partitions.  heres a look at my fstab, which had everything mounted correctly:

```

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=a4aa23d2-34f8-4048-a7fe-a9865463f374 / ext3 relatime,errors=remount-ro 0 1 #mounts correctly
# Entry for /dev/sda7 :
UUID=a13b2d59-43ea-4c0c-8eb0-6b6ab56e1f53 /backup/ ext3 relatime 0 2 #does not mount
# Entry for /dev/sda6 :
UUID=5d4c7b69-7b4d-46fa-b629-10bdcf5fafc1 /media/ ext3 relatime 0 2 #does not mount
# Entry for /dev/sda5 :
UUID=79a85a96-106d-4409-9d67-1b7ba6faa50f /music/ ext3 relatime 0 2 #mounts as sda6
# Entry for /dev/sda2 :
UUID=648bbe0c-f719-4fe4-85ef-1094d0abd2db none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda3 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

also, if i do mount /dev/sda5 /music, I get the contents of the ntfs partition I do not want to mount

---

### Post by meierfra. on 2010-03-09
I don't have much time right now, but have a couple of quick questions:

> I get the contents of the ntfs partition I do not want to mount

Is there anything on that partition you want to keep? 
Do you want that partition to be in the partition table?

---

### Post by ratcheer on 2010-03-09
> **dakoellis said:**
> I have what is a weird problem, at least I think it is.  I deleted some files and now my partitions do not show up in Gparted.  Instead, the entire disk shows up as unallocated space.  I am still able to run every partition, one of which is ubuntu and another which is Windows without any other apparent problems. 

I figure the problem would be a missing file that needs to be restored, but I have no idea what that might be.  any ideas?

Thanks

I reported this same problem on my system several weeks ago. I think everyone thought I was crazy.

Tim

---

### Post by dakoellis on 2010-03-09
> **ratcheer said:**
> I reported this same problem on my system several weeks ago. I think everyone thought I was crazy.

Tim

Did you get anywhere on the problem?

---

### Post by dakoellis on 2010-03-09
> **meierfra. said:**
> I don't have much time right now, but have a couple of quick questions:



Is there anything on that partition you want to keep? 
Do you want that partition to be in the partition table?

I'm sorry I was unclear.  it's not that I don't want the partition, I just have no need to mount it in ubuntu.  I do use it in windows.  I would like to keep all the files I have.  If I can get to a point in which all my data shows up again, I have no problem buying a new TB drive and copying it over into a correctly partitioned drive (I was planning on doing that anyway, just not quite so soon)

---

### Post by ratcheer on 2010-03-09
> **dakoellis said:**
> Did you get anywhere on the problem?

I'm afraid not.

Tim

---

### Post by meierfra. on 2010-03-09
> # Entry for /dev/sda7 :
UUID=a13b2d59-43ea-4c0c-8eb0-6b6ab56e1f53 /backup/ ext3 relatime 0 2 #does not mount
# Entry for /dev/sda6 :
UUID=5d4c7b69-7b4d-46fa-b629-10bdcf5fafc1 /media/ ext3 relatime 0 2 #does not mount


We know the start sector  of those two partitions:

/dev/sda7 : start=510931323, size=1024111557, Id=83
/dev/sda8 : start=1535042943, size=418477122, Id=83

(note here that the device names  in your original partition table and in fstab differ by one)

This should allow you to mount those partition even though they don't appear in the partition table:


```
media=$(sudo losetup -f --show -o $((510931323*512))  /dev/sda)
sudo mount -t ext3 $media /media
backup=$(sudo losetup -f --show -o $((1535042943*512))  /dev/sda)
sudo mount -t ext3 $backup /backup
```

The two partitions should now be mounted in /media and /backup.

---

### Post by meierfra. on 2010-03-09
I would like to apologize for getting you into this situation. I really should have told you to backup all  your Data before we started working on the partition table.

But I'm pretty confident, that mounting the two partition will work and that you will be able to recover all  your Data.

To summarize what has happened:

Your original partition table had two problem

[list=1]
[*] ```
/dev/sda3 * 50363775 258132[COLOR="Red"]473 [/COLOR]103884349+ 7 HPFS/NTFS
/dev/sda4 258132[COLOR="Red"]420[/COLOR] 1953520064 847693822+ f W95 Ext'd (LBA)
```

     /dev/sda3 ends after the start of /dev/sda4

[*]```

/dev/sda5 258132483 301202[COLOR="Red"]684 [/COLOR]21535101 7 HPFS/NTFS
/dev/sda6 301202[COLOR="Red"]685[/COLOR] 510931259 104864287+ 83 Linux

```
 /dev/sda5 starts right after /dev/sda6. Usually there is a 63 sector gap, but one needs at least  one sector in between to record the partition table.
[/list]

I had overlooked the second  problem and when we  used "sfdisk"   to fix the first problem,  "sfdisk"  could not find any good way to  write the new partition partition table and  dropped two of the partitions from the partition table.

I don't see anyway to fix your partition table, other than using "dd" to manually write a new partition  table.  

 So I suggest to proceed as follows:

1. Backup all your Data  to your new external drive (this assumes that the instructions from my previous post work)

2. Use "fdisk" to delete /dev/sda4 from the partition table. (that will also delete all the logical partitions.)

3.  Gparted should now recognize /dev/sda again and you should be able to recreated all the partitions

4.  update "fstab"

---

### Post by dakoellis on 2010-03-10
> **meierfra. said:**
> I would like to apologize for getting you into this situation. I really should have told you to backup all  your Data before we started working on the partition table.



you have no reason to apologize, because I know it's always a risk dealing with hard drive and partitions problems, and you should always backup information.  that being said, the final commands you gave me got me to the rest of my files, and I learned alot in the process.  I plan on backing up everything and just playing around with some of the ideas you had, and will probably end up just formatting the drive  into a large storage space.

Once again, I can't thank you enough for your time

p.s. should this be marked as solved?

---

### Post by meierfra. on 2010-03-10
> the final commands you gave me got me to the rest of my files,
Good. Now I feel better.

> I plan on backing up everything 
Good.

> and just playing around with some of the ideas you had,
I don't think this will get you anywhere.

>  and will probably end up just formatting the drive into a large storage space.

I don't think you need to delete Windows and Ubuntu (/dev/sda1 and /dev/sda3) but that is the cleanest solution.

> p.s. should this be marked as solved? 

I wouldn't.  I don't like to draw attention to threads using "sfdisk". I only use "sfdisk" if I don't see any other way to solve a problem. As one can see in this thread, it can easily mess up the partition even more.

---

