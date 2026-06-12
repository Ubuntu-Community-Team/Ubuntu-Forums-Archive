---
title: "Recover Lost or Corrupted GPT Partition"
date: 2012-04-10
forum: General Help
---

### Post by Aritsugu on 2012-04-10
Good Morning, Afternoon, Evening... delete as appropriate :)

I was hoping someone might take a look at a problem I'm having with an old drive I re-purposed to shuffle some data around on. Sadly it won't mount as it did before and   disk utility (Palimpsest) is saying there is just free space, no partition. I've been reading up on this stuff myself, but, I think I'm missing something, or I'm out of luck.

Not sure how this has happened, drive was formatted with a guid table and a single ext4 partition created on it, all within disk utility (Palimpsest). I moved the data over to it, powered down, moved drive to new machine, booted, partition gone, returned to first machine, still missing.

Note this isn't the boot disk.

The following sums up my attempts so far (not including my fruitless foray with testdisk)

gdisk (gpt fdisk) and fdisk with the following results:

```

dan@zeus:~$ sudo gdisk -l /dev/sda
[sudo] password for dan: 
GPT fdisk (gdisk) version 0.8.4

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sda: 625140335 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4FF348B9-D041-49A6-AD98-18C15F055F2D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  
dan@zeus:~$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

```Delving further into gdisk and following its suggestion I selected the 'v' (verify) option:

```

Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 625140335 sectors, needs to be 625142448 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: partition 1 is too big for the disk.

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.

Identified 4 problems!

```Its clearly a mess, for more info I've used the 'i' and 'p' options:
```

Command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 9E79F802-02B9-4097-8CD2-F9FFE96136BD
First sector: 34 (at 17.0 KiB)
Last sector: 625142414 (at 298.1 GiB)
Partition size: 625142381 sectors (298.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Command (? for help): p   
Disk /dev/sda: 625140335 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4FF348B9-D041-49A6-AD98-18C15F055F2D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  

```Following the suggestion of the 'v' (verify) command which said to use the 'e' option from the experts menu:
```

Command (? for help): x

Expert command (? for help): e
Relocating backup data structures to the end of the disk

Expert command (? for help): w

Warning! Secondary partition table overlaps the last partition by
2113 blocks!
You will need to delete this partition or resize it in another utility.

Problem: partition 1 is too big for the disk.
Aborting write operation!
Aborting write of new partition table.

```Since I'm not going to follow the advice to delete the partition (I need the data) I'll have a go at resizing it:
```

root@zeus:/home/brendan# parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? R                                                    
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? R                                                    
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? I                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? OK                                                             
Backtrace has 8 calls on stack:
  8: /lib/libparted.so.0(ped_assert+0x31) [0x7f8e8fe0c351]
  7: /lib/libparted.so.0(+0x444c1) [0x7f8e8fe3d4c1]
  6: /lib/libparted.so.0(ped_disk_new+0x75) [0x7f8e8fe13505]
  5: parted() [0x4070de]
  4: parted(interactive_mode+0xf3) [0x40e183]
  3: parted(main+0x8f) [0x40b1df]
  2: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f8e8f62bc8d]
  1: parted() [0x405709]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:718 in function _parse_header() failed.

Aborted


```Which causes parted to crash. Now I'm stuck, I also tried testdisk, and am willing to try anything to get this solved. I can see that the partition seems to be too big for the disk, so if I could just chop it smaller? I don't mind if that loses the files at the end as long as I get some of them back.

---

### Post by oldfred on 2012-04-10
I have not had to adventure into repairs of my gpt drives.

Have you backed up and tried these commands?

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by Aritsugu on 2012-04-10
I did read the information on the link you provided. The most relevant part is "probably" 

"If the original disk used an unusual partition table size, though, you'll need to resize your in-memory table before you can successfully load the table from disk."

I say "probably" as they might mean the size of the table or the partition, its the partition in my case that appears to be a unusual size. 

Like I say I'm confused now, if I can resize the partition like the gdisk utility suggests, great, but parted crashes simply loading the information.

if I resize will it ruin the information on the drive or will it crop the end off? the later I can cope with.

I'm guessing I should 'dd' the drive. I'll work out the command, it'll have to be to a file as I don't have a spare drive.

I'm off to bed now, I'll check in again at 0900 UTC, thanks guys.

---

### Post by Aritsugu on 2012-04-11
Warning: don't do what I'm doing, because I don't have a clue what I'm doing! 

Not sure if backing up a broken partition table makes sense, but I guess its all I've got so I guess I'll keep it... despite all the warnings it says it completed successfully so I guess I should trust it...  (note its sgdisk I'm using, not sfdisk which didn't work on gpt disks).

After this I'm off to find/buy a spare harddrive to clone the broken disk to, I guess using ddrescue, something like:

ddrescue /dev/sda /dev/sdb logfile 

However from the ddrescue manual :

"Note: you do not need to partition /dev/hdb beforehand, but if the partition table on /dev/hda is damaged, you'll need to recreate it somehow on /dev/hdb.  "

This applies to me I guess, not sure what to do about it though. If I created a new partition etc on the new disk and copied the damaged one over would I be back in business? can I even copy the partition off the damaged drive? 
 
Off to find a harddrive to clone onto, output of sgdisk partition table backup follows:

```
root@zeus:/home/dan# sgdisk -b sda-backup.gpt /dev/sda
Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
The operation has completed successfully.
```

---

### Post by Aritsugu on 2012-04-11
Ok I found a dusty old drive to clone onto, smart is saying it has a uncorrectable sector, and a pending sector, but, hey worth a shot. Plus side its the same size as my problem drive.

I've followed the same approach to partitioning this new drive as the problem drive and then had a look at it with gdisk. 

The disk utility has partitioned it the same, starting (34) and ending (625142414) on the same sectors. But this drive claims to have 625142448 sectors, which is enough to fit the old partition in, while the current drive is reporting  625140335 sectors, too small for the partition to end on 625142414. I'm guessing this is the problem?! The problem drive is no longer reporting the same number of sectors as it did when I partitioned it? Hence the backup partition table has been lost, causing the drive not to mount, the crc errors, can't be rewritten and etc.

Ok so I'm waiting for the result of:

root@zeus:/home/brendan# dd_rescue -l ddlogfile /dev/sda /dev/sdd

I realise this will overwrite the partition I just created but hey! hopefully because this drive is reporting that it is big enough for the partition it will be file and dandy...

we are at 6% (that's the royal we)

```

root@zeus:/home/brendan# gdisk /dev/sdd
GPT fdisk (gdisk) version 0.8.4

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sdd: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 58F7115C-D8E0-4D86-B93A-1421EE9F14B8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  

Command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 472AD041-C293-4BDE-BF64-46E5A6AB964A
First sector: 34 (at 17.0 KiB)
Last sector: 625142414 (at 298.1 GiB)
Partition size: 625142381 sectors (298.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Command (? for help): v

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.

No problems found. 0 free sectors (0 bytes) available in 0
segments, the largest of which is 0 (0 bytes) in size.

Command (? for help): q

```

---

### Post by oldfred on 2012-04-11
I think that srs5694 (same fellow as the rodbooks site) said not to use dd with gpt partitions. Something about the internal structure of the partition and the gpt tables. You can use dd on the entire drive as then all the internal structures and tables are also copied.

---

### Post by Aritsugu on 2012-04-11
Thanks, oldfred

I think dd'ing /dev/sda to /dev/sdd where sda and sdd are both 320GB drives should copy all of the gpt and partition data (byte for byte?). creating an exact copy???

My only concern is I should have used dd not dd_rescue? as is suggested on the rodbooks site, also, the rodbooks repair site states w.r.t. dd 

> Note that if the backup disk is larger than the source, even by a single sector, the GPT backup data structures will be misplaced on the backup disk. This can make GPT data recovery harder, so you may need to work on the original disk rather than the backup.

Now I know it is bigger, by about 2000+ sectors but the backup GPT structures are already broken/missing on the original and need to be replaced anyway. I think. and since the old disk seemed to shrink (was possibly the same size as the new one initially ) and not allow the backup structures to be written to the end of the partition, the new drive being bigger is surely a good thing??

I'm enjoying making all this up as I go along. 

the backup using dd_rescue is at 62% complete, so its going to be about another hour and a half before I can have a play with this. 

PS. I'm surprised the log file is empty.

---

### Post by oldfred on 2012-04-11
I thought dd_rescue was just a front end for dd, so I would not worry about that.

Keep us posted. All I can offer is moral support as you are well past what I know.

---

### Post by Aritsugu on 2012-04-11
The following is the result of the dd_rescue command looks good to me...

```
root@zeus:/home/dan# dd_rescue -l ddlogfile /dev/sda /dev/sdd
dd_rescue: (info): ipos: 312570112.0k, opos: 312570112.0k, xferd: 312570112.0k
                   errs:      0, errxfer:         0.0k, succxfer: 312570112.0k
             +curr.rate:    17727kB/s, avg.rate:    29535kB/s, avg.load:  5.9%
dd_rescue: (info): /dev/sda (312570176.0k): EOF
Summary for /dev/sda -> /dev/sdd:
dd_rescue: (info): ipos: 312570176.0k, opos: 312570176.0k, xferd: 312570176.0k
                   errs:      0, errxfer:         0.0k, succxfer: 312570176.0k
             +curr.rate:     2897kB/s, avg.rate:    29535kB/s, avg.load:  5.9%

```

On the off chance I've checked the disk utility and its not saying anything new about the drive.

I'm going to try a windows trick, reboot....

---

### Post by Aritsugu on 2012-04-11
oldfred, 
simply your presence let alone your technical and moral support is most welcome. During times of stress its generally advisable to have someone there for you. I'd have talked to the missus but since the photos of her sister's wedding are on this drive I thought it would be best to fix the problem, rather than discuss it :)

The good news is I think I've dodged a bullet on this one, I can mount the backup, and I can copy a file off it :guitar:...............

"sudo gdisk /dev/sdd" however is not entirely happy, noting that the disk guid in the backup header is different from the main header (see output below). The one in the main header is from the original 'problem' disk, whereas the backup header contains the guid for the new disk. Makes sense to me, dd didn't overwrite the backup header on the new disk as it finished copying the old 'shorter' disk first. Now I guess I can get rid of these warnings by over-writing the backup with the main header. However I would think that would leave me with two disks with the same disk guid? A problem perhaps? 

First things first I'm going to copy the files off onto a newer drive, after that I don't care to fix it any further,  both drives are going in the not trusted pile, for eventual sledgehammering, but once I'm sure the files are off, I could 

a) use gdisk to overwrite the backup header on the backup drive and see what happens... will the warnings disappear? 

EDIT: The following is wrong there isn't a resize partition option, there is a resize partition table option. (Aritsugu)
_[COLOR=Red]b) I could brave the resize option (I just noticed) on the gdisk utility to shrink the partition on the original drive so it fits on the disk[/COLOR]_, see if it mounts then, and how much data is lost....

Regardless that's for doing once the copying is done, see you in a few hours.

BTW I'm hoping that my degree of verbosity is going to be helpful rather than annoying, let me know if its the later...  

```
Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: main header's disk GUID (4FF348B9-D041-49A6-AD98-18C15F055F2D) doesn't
match the backup GPT header's disk GUID (58F7115C-D8E0-4D86-B93A-1421EE9F14B8)
You should use the 'b' or 'd' option on the recovery & transformation menu to
select one or the other header.

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

```

---

### Post by oldfred on 2012-04-11
Keep us updated, it may help someone searching in the future or we can pass along the info.

I would also try fixes, just to see if they work. Then if that happens again we have a quicker(?) way to repair.

---

### Post by Aritsugu on 2012-04-11
Sure thing, I'll try the fixes I've proposed, once the data is safe (about an hour away, that's USB2 for ya). I'm interested in the outcome myself. Though I'd venture that resizing the damaged partition in situ, even if it works this time, would be more dangerous than what we did here.

If I try the resize and it doesn't work do I still mark as solved? since I got the data off, I'm guessing yes. But then if a tree ...

---

### Post by Aritsugu on 2012-04-12
OK, I'm going to explore this a bit further, for prosperity sake.

a quick recap of where we stand

  orig-drive (320GB Hitachi): I formatted with ubuntu's disk utility (on 11.10) using a guid partition table, and created one big ext4 partition, moved a bunch of mixed type data (295GB) to it. shutdown, removed drive, walked to 2nd computer, installed, booted, discovered drive was listed as free space. doh! gdisk returned a bunch of errors, but it seemed to me (I'm no expert) that the big problem, and why the computer wouldn't mount the partition was that it ended on a higher sector than possible for the number of sectors on the drive. In addition the backup gpt header was also situated after the last possible sector. Trying to rewrite the backup header (using gdisk) didn't work as the disk was not big enough. 

backup-drive (320 GB): is a second drive I formatted with ubuntu's disk utility (on 11.10) using a guid partition table, and created one big ext4 partition. Used this to compare partition table structure with original drive.

Used dd_rescue to copy orig-drive to backup-drive, which despite having the same size on the label, reported a few more sectors. Following this I was able to mount resulting drive and get data off.

Now I'm going to see what happens when I try a couple of other options with the drives.

Firstly, using gdisk on the backup-drive, complains that the disk guid in the main header doesn't match the disk guid in the backup header. Comparing the information in both shows the only difference is the disk guid, so I've opted to copy the backup header over the top of the main header. My thinking is as follows: I don't want two disks with the same guid, the rest of the information is the same, so no harm done (I also made a backup of the partition table to a file before hand using gdisk). This has worked. gdisk is no longer complaining. drive mounts, data accessible.

Just noticed you can change the disk guid in the extra (x) expert menu of gdisk, could be useful for dealing with this.

```

root@zeus:/home/dan# gdisk /dev/sdd
GPT fdisk (gdisk) version 0.8.4

Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: main header's disk GUID (4FF348B9-D041-49A6-AD98-18C15F055F2D) doesn't
match the backup GPT header's disk GUID (58F7115C-D8E0-4D86-B93A-1421EE9F14B8)
You should use the 'b' or 'd' option on the recovery & transformation menu to
select one or the other header.

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.

Identified 2 problems!

Command (? for help): r

Recovery/transformation command (? for help): p
Disk /dev/sdd: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4FF348B9-D041-49A6-AD98-18C15F055F2D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  

Recovery/transformation command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 9E79F802-02B9-4097-8CD2-F9FFE96136BD
First sector: 34 (at 17.0 KiB)
Last sector: 625142414 (at 298.1 GiB)
Partition size: 625142381 sectors (298.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Recovery/transformation command (? for help): m

Command (? for help): b
Enter backup filename to save: gptpart-rd.gpt
The operation has completed successfully.

Command (? for help): r

Recovery/transformation command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 9E79F802-02B9-4097-8CD2-F9FFE96136BD
First sector: 34 (at 17.0 KiB)
Last sector: 625142414 (at 298.1 GiB)
Partition size: 625142381 sectors (298.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Recovery/transformation command (? for help): p   
Disk /dev/sdd: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4FF348B9-D041-49A6-AD98-18C15F055F2D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  

Recovery/transformation command (? for help): b

Recovery/transformation command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 9E79F802-02B9-4097-8CD2-F9FFE96136BD
First sector: 34 (at 17.0 KiB)
Last sector: 625142414 (at 298.1 GiB)
Partition size: 625142381 sectors (298.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Recovery/transformation command (? for help): p
Disk /dev/sdd: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 58F7115C-D8E0-4D86-B93A-1421EE9F14B8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  

Recovery/transformation command (? for help): b

Recovery/transformation command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.

Identified 1 problems!

Recovery/transformation command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT) to /dev/sdd.
The operation has completed successfully.
root@zeus:/home/dan# gdisk /dev/sdd
GPT fdisk (gdisk) version 0.8.4

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sdd: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 58F7115C-D8E0-4D86-B93A-1421EE9F14B8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34       625142414   298.1 GiB   0700  

Command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 9E79F802-02B9-4097-8CD2-F9FFE96136BD
First sector: 34 (at 17.0 KiB)
Last sector: 625142414 (at 298.1 GiB)
Partition size: 625142381 sectors (298.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Command (? for help): q
root@zeus:/home/dan# 
```The second thing I wanted to try was to fix the original disk, in place, possibly by resizing the partition so it fit the size the disk is now reporting. I had said there is a resize facility in the gdisk menu but actually its to resize the partition table, not the partition. And since parted crashes on inspecting this disk, I guess we are done here. I would have liked a solution to recovering the original disk without needing the second same sized disk but, hey, I got my data off. 

Feel free to chime in, and correct any noob mistakes I've made.

---

### Post by oldfred on 2012-04-12
The only thing I found that might work, but I only suggest it if you have given up on everything else as I really do not know.

gdisk also has sgdisk
[http://www.rodsbooks.com/gdisk/sgdisk.html](http://www.rodsbooks.com/gdisk/sgdisk.html)

**-d, --delete=partnum**   Delete a partition. This action deletes the entry from the partition table [COLOR=Red]but does not disturb the data within the sectors[/COLOR] originally allocated to the partition on the disk. If a corresponding hybrid MBR partition exists, **gdisk** deletes it, as well, and expands any adjacent 0xEE (EFI GPT) MBR protective partition to fill the new free space. 

then create a new partition with the correct size?


**-n, --new=partnum:start:end**   Create a new partition. You enter a partition number, starting sector, and an ending sector. Both start and end sectors can be specified in absolute terms as sector numbers or as positions measured in kibibytes (K), mebibytes (M), gibibytes (G), tebibytes (T), or pebibytes (P); for instance, **40M** specifies a position 40MiB from the start of the disk. You can specify locations relative to the start or end of the specified default range by preceding the number by a '+' or '-' symbol, as in **+2G** to specify a point 2GiB after the default start sector, or **-200M** to specify a point 200MiB before the last available sector. A start or end value of 0 specifies the default value, which is the start of the largest available block for the start sector and the end of the same block for the end sector. A partnum value of 0 causes the program to use the first available partition number.

---

### Post by trusktr on 2012-12-03
I have the same or similar problem. What I did was clone a 750Gb windows drive to a smaller disk by first shrinking the huge data partition and moving all partitions as close to the start of the disks as possible using gparted to make sure the partitions end before the size of the small disk, then copying the big disk to the small disk using dd.

After plugging the small disk in to my linux box, then gdisk shows the exact same warning/error messages. I bet, for some reason, you can't simply dd gpt disks when the disk sizes vary...

Attempting to boot windows from the smaller cloned drive doesn't work. :(

If I find a solution I'll post here.

---

### Post by trusktr on 2012-12-03
For me, the fix was easy. I went into gdisk's expert mode, then I ran the 'e' command to relocate the backup GPT table to the end of the disk (an obvious thing to do knowing how GPT works now, and that the disk sizes were of different size). Then, I used 'w' to write changes and exit. Problem fixed!

More details here: [https://bbs.archlinux.org/viewtopic.php?pid=1201526](https://bbs.archlinux.org/viewtopic.php?pid=1201526)

---

### Post by rfair404 on 2013-03-07
I just updated from 10.04 to 10.04 and am now unable to mount my secondary (storage only) drive. 

Here is what I get when I run gdisk -l /dev/sda

```
 
GPT fdisk (gdisk) version 0.8.1

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sda: 1953523055 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B0A76717-E1A2-4FA0-A5B6-D37CDE96D617
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 5070 sectors (2.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2              34      1953520064   931.5 GiB   0700  

```

Any suggestions on this would be helpful.

---

### Post by oldfred on 2013-03-07
Have you tried the gdisk experts mode and the commands posted above?

---

### Post by rfair404 on 2013-03-08
We'll yes and no. I have run the gdisk application and got to the experts menu, just not sure which commands to run. I (think I) Backed up the old partition data. 

I haven't looked at using the dd tools yet as I don't have another drive big enough to clone this one to (1tb). 

Should I start with 

```
gdisk /dev/sta
r
x
e
w
```

or 

```
gdisk /dev/sda
r
c
w
```

?

---

### Post by oldfred on 2013-03-08
I have several gpt drives, but never have had to run the experts commands to repair them. 

If you have good backups, you should be ok. 

If any command does not seem to give good results do not issue the w so it does not write the changes.

---

