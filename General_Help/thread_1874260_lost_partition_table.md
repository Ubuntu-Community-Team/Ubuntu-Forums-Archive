---
title: "lost partition table"
date: 2011-11-02
forum: General Help
---

### Post by sir.hampster on 2011-11-02
Hello everyone,
earlier today for the first time in years I tried to access my ext4-FS from Win7 using Ext2read and Ext2fsd. After that my partition table was gone and grub complained about not having any partition to boot from.

I managed to recover the table using testdisk after which grub booted ok. However, I'm left with two problems:

1) gparted shows the whole disk now as "unallocated" stating the warning "Can't have a partition outside the disk!".

2) I had a truecrypt partition on /dev/sda6, which is currently unavailable because Testdisk does not seem to have restored its entry on the partition table.

This is what Testdisk sees, the truecrypt partition is supposed to be inside the extended sda4 after the swap (sda5).
> ```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 44514 254 59  715133408
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 2 P HPFS - NTFS          44515  23 53 44527 214 39     204800 [System Reserved]
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 3 P HPFS - NTFS          44527 214 40 57568 223 63  209504256
 4 E extended LBA         57568 225  1 60801 254 63   51940035
 5 L Linux Swap           57569   0  1 58090 254 45    8385912

```



Any help for my problems would be very much appreciated! :)

---

### Post by coffeecat on 2011-11-02
> **sir.hampster said:**
> 1) gparted shows the whole disk now as "unallocated" stating the warning "Can't have a partition outside the disk!".

It's very common for testdisk to restore the partition table with the last sector of an extended partition seemingly beyond the last physical sector of the drive. Gparted reacts to this impossibility by reporting the whole disc as unallocated. If this is what has happened, this is easily fixed. Post the output of:

```
sudo fdisk -lu
```

I'll post a couple of links now, which will be relevant if this is what the problem is.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I have no experience of truecrypt so I won't be able to help you with that.

---

### Post by sir.hampster on 2011-11-02
thank you, coffeecat!
I have started reading those pages about fixparts. I'm not too familiar with partitioning though, so I have no idea what those GPT data is they are talking about. It makes me worry that maybe my truecrypt partition might be seen as such GPT!? I don't want it to be deleted... there are some rather important things in the truecrypt partition.

However, here my fdisk dump as you requested:

```
:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f6dab64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   715133470   357566704   83  Linux
/dev/sda2       715134976   715339775      102400    7  HPFS/NTFS/exFAT
/dev/sda3       715339776   924844031   104752128    7  HPFS/NTFS/exFAT
/dev/sda4       924844095   976784129    25970017+   f  W95 Ext'd (LBA)
/dev/sda5       924845985   933231896     4192956   82  Linux swap / Solaris

```

---

### Post by coffeecat on 2011-11-03
Here's your problem:

> **sir.hampster said:**
> ```
:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Red"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f6dab64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   715133470   357566704   83  Linux
/dev/sda2       715134976   715339775      102400    7  HPFS/NTFS/exFAT
/dev/sda3       715339776   924844031   104752128    7  HPFS/NTFS/exFAT
/dev/sda4       924844095   [COLOR="Red"]976784129[/COLOR]    25970017+   f  W95 Ext'd (LBA)
/dev/sda5       924845985   933231896     4192956   82  Linux swap / Solaris

```

It's what I thought it would be, based on the "Can't have a partition outside the disk!" message from Gparted. The end sector of the extended partition sda4 is recorded as 976784129, which does not exist, being beyond the 976773168 sectors of the whole drive.

Fixparts will fix this easily. The GPT thing is mentioned in the Fixparts page because fixparts is designed to deal with several partition table problems, residual GPT data in a MBR partition table being only one of them. You have a MBR partition table.

With regard to your truecrypt partition, there is no entry in the partition table for it, possibly because testdisk was not able to find it. There is, however, a gap of about 22GB between the end of sda5 and the end of the drive. I guess this is where sda6 is/was. 

Testdisk has a "deep scan" option which may or may not find it. The problem with a deep scan is that it can find residua from long-deleted partitions and you have to examine the output of testdisk carefully before letting it proceed. Whether you should run fixparts to fix the extended partition anomaly first and then run testdisk again to try to find the truecryt partition, or whether you could do a deep scan with testdisk first, I don't know. If you run fixparts first and then testdisk, it *may* introduce the same anomaly again.

Whichever you do, backup your current partition table data with sfdisk (not fdisk) first as described in both the links. Or make sequential backups at each stage of your recovery process. They are only small text files and there are instructions in the first link to write them back to the partition table if things go really wrong.

Fixparts won't delete your truecrypt partition any more than it is missing at the moment. As I understand it, truecrypt acts at the file or partition level. Your immediate problem is a single inconsistency in the partition table, and fixparts works on the partition table which is physically near the beginning of the drive. The other problem is the current failure of testdisk to find sda6, and fixparts won't make that any better or any worse.

---

### Post by sir.hampster on 2011-11-03
Thank you coffeecat!

I tried using the deep scan with testdisk, but all it found were impossible large partitions at the end, so no truecrypt partition

I used fixparts with success, but all it did was wrapping the extended partition around my /sda5, so I started playing around with sfdisk myself:

I noticed that when using "sfdisk -f < parts.txt" to use the backup, it already warns about the too large partition size and even gives the maximum possible size, so I edited the parts.txt directly, adjusting for the highest possible size and it set the extended partition as it should be! :D

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=715133408, Id=83, bootable
/dev/sda2 : start=715134976, size=   204800, Id= 7
/dev/sda3 : start=715339776, size=209504256, Id= 7
/dev/sda4 : start=924844095, size= 51929073, Id= f
/dev/sda5 : start=924845985, size=  8385912, Id=82
```

This worked fair enough, so I added the sda6 manually using
```
/dev/sda6 : start=933231897, size= 43541271, Id= 0
```
unfortunately this didn't work for truecrypt... guess I will have to go to the truecrypt forum now.

thanks again!

---

### Post by coffeecat on 2011-11-03
Good luck with the Truecrypt forum. I notice that you've set the id for sda6 as 0. If I remember correctly, that's the code used for an empty partition with no filesystem. You might need to use the code for whatever filesystem it was before you truecrypted it.

---

### Post by oldfred on 2011-11-03
There is this also.
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

And I think this is the command line version since it still is parted.
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

But I believe gparted (and parted?) have see encrypted partitions as unformatted space, so it may not work.

---

### Post by sir.hampster on 2011-11-03
hey, thanks to the both of you!

@coffeecat: I used type 0 (=unused) because I didn't know and couldn't find out the partition type truecrypt uses.


I have read some bits in the truecrypt forum, unfortunately I can't go on their nerves because I don't have a valid email for them at the moment, so I can't post there, only read...

However, what I read so far is that truecrypt partitions are quite hard to see for tools like gparted or testdisk and their solution is to use WinHex and search for the partition by hand.

I actually managed to find it (using WinHex on Windows7)! My manually created /sda6 was way too big, lots of zeroes at the beginning and the end of /sda6. but the zeroes made it easy to locate the random data from the partition. a nice set of 20.76 GiB which sounds about right to me.

As suggested on the truecrypt forum, I extracted the first ~20KiB from that and tried mounting as a truecrypt container with my password and it went past the "Incorrect password or not a TrueCrypt volume" so my password matches with the truecrypt header. :)


Now I'm looking for a way of dumping those 20.76 GiB into a nice image file before trying to create a matching partition entry. WinHex only allows up to 200KB file extractions in the trial version.

Could dd do this? I have looked into its manual, but haven't found anything I understand in this regard...

This is the portion:
```
                       Start            End

Cylinder No.           61721            64601
Head No.                 166               14
Sector No.                 1               63
Block (Offset)    6F3FFAD400       74709881FF
```doing my math the size is:
74709881FF - 6F3FFAD400 = 5309DADFF
500,105,249,279 - 477,814,772,736 = 22,290,476,543 ~= 20.759624 GiB

---

### Post by oldfred on 2011-11-03
I always hesitate to use dd, but some info:

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

And I think you started to use sfdisk to create partition.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

caljohnsmith and meierfra were the original creators of the boot_info script and seem to know the inner working very well.

---

### Post by sir.hampster on 2011-11-03
I just tried this, but didn't work:

```
:~$ sudo dd if=/dev/sda of=/home/nc/Desktop/mydump.iso bs=512 seek=477814772735 count=22290476543
dd: failed to truncate to 244641163640320 bytes in output file `/home/nc/Desktop/mydump.iso': File too large
```

---

### Post by oldfred on 2011-11-03
I really do not know dd, but did you tell it you want 
22290476543 blocks of 512 bytes each?

---

### Post by sir.hampster on 2011-11-04
ah, thanks oldfred for the topic about DD!


didn't divide the blocks by the block size.. 

```
:~$ sudo dd if=/dev/sda of=/home/nc/Desktop/mydump.iso bs=512 skip=933231978 count=43536087 conv=notrunc,noerror
43536087+0 records in
43536087+0 records out
22290476544 bytes (22 GB) copied, 919,256 s, 24,2 MB/s
```
worked like a charm :) and I can mount the iso with truecrypt!

---

### Post by sir.hampster on 2011-11-04
and using sfdisk again I managed to get my truecrypt partition back using:
```
/dev/sda6 : start=933231978, size= 43536087, Id= 0
```

truecrypt doesn't care about the partition type ;)

thanks to everyone! *solved*

---

### Post by oldfred on 2011-11-04
It looks like you  solved this on your own, I just kinda pointed you in the right direction. 

Now you can come back an help others with similar issues.:)

---

