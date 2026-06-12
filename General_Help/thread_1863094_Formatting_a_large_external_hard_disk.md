---
title: "Formatting a large external hard disk"
date: 2011-10-17
forum: General Help
---

### Post by bluebelle on 2011-10-17
It seemed easy enough, I needed to save tons of backups and grabbed a couple of WD My Book Essentials 3TB external drives from a local store. Came home to start copying my files and spent the next 3 hours trying to format the damn things. Unsuccessfully.

I must warn you that although I have been using Linux for a long time, the last 2 years or so have been not very hard core and my skills must be rustier than I'd like to admit. I started using **cfdisk** at first, before realizing that something is fishy, looking up online and finding out that I should use **parted** instead for a drive this size.

I found this easy looking tutorial [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html) and proceeded, only to have **parted** crash and burn on me when I issue command: **[COLOR=#0000ff]mklabel gpt[/COLOR]** Some kind of stack error. Long error log. I fire up gparted instead and that refuses to open up at all, leaving, among other things, a message:
*Warning: Device /dev/sdb has a logical sector size of 4096. Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.*

Not sure if that was the reason it crashed, but it's the only thing I could make sense of. 

I'm running karmic, if that matters. Updated the system, restarted, did not help. Any ideas how to tackle this would be appreciated.

---

### Post by mreos on 2011-11-15
Hello everyone!

I'm hoping the gurus here can help guide me.

Here's what I did:
-boot PC to usb flash drive and clicked on Try Ubuntu
-plugged in new external usb 3TB Western Digital Mybook
-launch Disk Utility and selected Format Drive
-Selected Scheme: GUID Partition Table and then clicked on Format

After several seconds, I get a pop up with this message:

> Error creating partition table: timeout (10s) waiting for changeWhat did I do wrong?

TIA

---

### Post by jjex22 on 2011-11-15
There's been a bit of talk about trouble with drives over 2.2tb, looks like [partedmagic's]("http://partedmagic.com/doku.php") latest version isn't having any issues with it, so maybe try using that to format? then run the installer again and just mount the ext4 partion(s) as you want them?

---

### Post by Cyclane on 2011-11-15
I'm feel sorry that I'm hijacking this thread but jjex22, does this only concern the disk-utility of ubuntu, or does this also affect fdisk & mkfs in the terminal?

---

### Post by jjex22 on 2011-11-15
I'm not completely sure - as far as I knew fdisk was fine, it was the installer and gparted that were having issues, but I'd not read anything on it for a while so assumed support had been improved in recent releases.

Perhaps we can get mreos to confirm after install?[-o<

---

### Post by mreos on 2011-11-17
Thanks for the info jjex22.

I guess it was a bad decision on my end to buy a 3TB drive thinking it would be easy to use in Ubuntu (11.10 64bit) like any other drive.  To make matters worse, all the technical details out there about large drives makes it more confusing.

Can anyone confirm if my steps above are correct? I just want to be able to format it so that it is clean and can be used for storage on windows and ubuntu PCs.

---

### Post by mreos on 2011-11-17
I saw your post and was wondering if you found a solution. I also have a 3TB WD Mybook.

---

### Post by coffeecat on 2011-11-17
@mreos, I notice that bluebelle has not logged in since posting or since shortly after posting, so you may or may not get a reply.

I have no experience of drives > 1TB but I wonder if the OP's problem is a combination of a drive with 4k sectors (which a 3TB drive would have) and using partitioning tools from an obsolete version of Ubuntu which would probably only cope with 512-byte sectors. The OP was right in trying to create a GUID partition table but was using the now-obsolete Ubuntu Karmic.

Which version of Ubuntu are you using and have you created a GUID partition table?

---

### Post by Cyclane on 2011-11-17
From the information I gathered here. You could split your drive in two by making two partitions. these partitions can be formatted into the fs of your choice.

---

### Post by Cyclane on 2011-11-17
Might have drawn my conclusion a but to quick. Let me ask this first.

What is it that you want to do with your external hd? Is it only for storage or do you want the to install anything on it?

---

### Post by Cyclane on 2011-11-17
Might have drawn my conclusion a but to quick. Let me ask this first.

What is it that you want to do with your external hd? Is it only for storage or do you want the to install anything on it?

---

### Post by scottbomb on 2011-11-17
If you want Windows to have read/write access to it, you'll need to format at least 1 partition in NTFS. Create the partition in Windows (left-click My Computer -> manage) and if you want to leave some space for a Linux OS, you can leave some unallocated space on the drive where Ubuntu will happily set up ext4.

---

### Post by oldfred on 2011-11-17
I have used gpt, but on smaller drives. I have saved these links, so I would know what to do in the future with a larger drive.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)
The emergency disks that include GPT fdisk are:
    * SystemRescueCd
    * PartedMagic 
sudo parted /dev/sda unit s print
gdisk -l /dev/sda
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

How to install a WD Advanced Format Drive on a non-Windows Operating System
the following distributions will default to good alignment for Advanced Format disk drives: Ubuntu 10.04, Fedora 13, Redhat 6 and derived products. 
[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)

---

### Post by mreos on 2011-11-17
Thank you all for your replies

Cyclane - I would like to use it for storage and file transfer between different PCs that are running different OS.

scottbomb - is partition necessary? i would like to use it as one big drive.

oldfred - thanks for the links. I will try to make sense of all the technical details.

---

### Post by mreos on 2011-11-17
Hi coffeecat

I am using ubuntu 11.10 64bit and still learning.  

How can I confirm if I have a GUID partition table?  I already attempted to format different ways and am lost.

---

### Post by oldos2er on 2011-11-17
Threads merged. Please don't start more than one thread per topic.

---

### Post by oldfred on 2011-11-17
If it is gpt, fdisk should just give a warning.
sudo fdisk -lu

This  works with both MBR & gpt.

sudo parted /dev/sda unit s print

And this is the gpt version of fdisk that works on gpt:
gdisk -l /dev/sda
```

fred@fred-MavericDT:~$ sudo parted /dev/sda unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=Red]msdos[/COLOR]

Number  Start       End         Size        Type     File system  Flags
 1      63s         115330634s  115330572s  primary  ntfs         boot
 4      115330635s  156296384s  40965750s   primary  fat32
 2      156296385s  312576704s  156280320s  primary  ext3

fred@fred-MavericDT:~$ sudo parted /dev/sdb unit s print
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=Red]gpt[/COLOR]

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s                                bios_grub
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4

```

---

### Post by mreos on 2011-11-18
> **oldos2er said:**
> Threads merged. Please don't start more than one thread per topic.

Not sure why my thread was merged with the other member.  The replies now look disconnected.  I thought if I have my own issue (error) that I should create my own thread. If I'm wrong, let me know so I know for next time.  Thank you.

---

### Post by mreos on 2011-11-18
> **oldfred said:**
> If it is gpt, fdisk should just give a warning.
sudo fdisk -lu

This  works with both MBR & gpt.

sudo parted /dev/sda unit s print

And this is the gpt version of fdisk that works on gpt:
gdisk -l /dev/sda



I used the command you listed and here is what it shows

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sda: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   732558335  2930233340   ee  GPT

```

Sorry for this dumb question, but what do I do next with disk utility?  Just click format drive and then format volume? My error is probably because I didn't choose the right options.

Thank you for your time oldfred

---

### Post by oldfred on 2011-11-19
I have used gparted on smaller drives, and selected gpt under device, advanced select gpt.

But I suggest downloading gdisk either from the Ubuntu repository or to get the newest version from the rodbooks site.

---

### Post by coffeecat on 2011-11-19
> **mreos said:**
> Not sure why my thread was merged with the other member.  The replies now look disconnected.  I thought if I have my own issue (error) that I should create my own thread. If I'm wrong, let me know so I know for next time.  Thank you.

You started your own thread and posted a question on another thread about essentially the same issue, and received replies in both. This dilutes community effort.

---

### Post by mreos on 2011-11-20
Is there a bug in Ubuntu?

Also, there seems to be a lot of headaches caused by these 3TB drives as evident when searching on the web for solutions.

I used gparted from bootable USB (Ubuntu 11.10 64bit) and I think I finally have a GPT partition

***_but_*** when I go into disk utlity and look at the info, the partition type shows:

Model: WD My Book 1140
Firmware Version: 1003
Capacity: 3.0 TB (3,000,558,944,256 bytes)
Partitioning: [COLOR=Red]**Unknown Scheme:**[/COLOR]
Usage: Filesystem
Partition type: [COLOR=Red]**Unknown ()**[/COLOR]
Type: Ext4 (version 1.0)

I then launch gparted and the device information shows:
Model: WD My Book 1140
Size: 2.73 TiB
Partition table: gpt
Heads: 255
Sectors/track: 63
Cylinders: 45599
Total sectors: 732558336
Sector size: 4096

The external drive is plugged into the USB 3.0 port.  Because of the unknown, I'm afraid to start copying files onto the external drive.

---

### Post by oldfred on 2011-11-20
On my small drives Disk Utility shows gpt. Perhaps something about the 4K sectors?

What does this show?

sudo parted /dev/sda unit s print

---

### Post by mreos on 2011-11-20
> **oldfred said:**
> On my small drives Disk Utility shows gpt. Perhaps something about the 4K sectors?

What does this show?

sudo parted /dev/sda unit s print


Here's the output for the 3TB:

```
Model: WD My Book 1140 (scsi)
Disk /dev/sda: 732558336s
Sector size (logical/physical): 4096B/4096B
Partition Table: gpt

Number  Start  End         Size        File system  Name  Flags
 1      256s   732558079s  732557824s
```As a test, I tried it on a much smaller drive and I'm _assuming this is what I should be seeing_:

disk utility shows:
Partitioning:**[COLOR=Navy]GUID Partition Table[/COLOR]**
Usage: Filesystem
Partition type: [COLOR=Navy]**Linux Basic Data Partition**[/COLOR]

gparted shows:
Partition table: **[COLOR=Navy]gpt[/COLOR]**

---

### Post by oldfred on 2011-11-20
It looks like you have a partition that is unformated? Did you format it to NTFS or ext4?

What you see on your smaller drive is exactly what I see on my two gpt drives that are 160GB & 60GB.

```
fred@fred-MavericDT:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10

```

---

### Post by mreos on 2011-11-20
Very strange how disk utility is showing something different than what gparted is showing

I've attached screens from both utility and gparted

---

### Post by oldfred on 2011-11-20
My guess ( I do not really know) is that Disk Utility is not truly updated for gpt for 4K drives. It seems to show gpt smaller drives ok. I think gparted then is more reliable. 

My only concern then is what else is not updated for the new 4K drives. I have seen some issues on smaller external drives with 4K which did not seem necessary. 

The WD site says all new kernels are updated, so it should work, but then some utilities may not.

What does gdisk show?

```
fred@fred-MavericDT:~$ sudo gdisk /dev/sdd -l
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  10
```

---

### Post by mreos on 2011-11-20
> **oldfred said:**
> 

What does gdisk show?



I copy and paste your command but get this:

```
sudo: gdisk: command not found
```Update: I was able to find and [install fdisk]("https://launchpad.net/ubuntu/oneiric/amd64/gdisk/0.6.14-1") from here (thought it was part of ubuntu)

I'm getting this for output:
```
 GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 732558336 sectors, 2.7 TiB
Logical sector size: 4096 bytes
Disk identifier (GUID): A1634F7C-96A4-48D9-B73C-BC91D10FFAF3
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 732558330
Partitions will be aligned on 256-sector boundaries
Total free space is 501 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1             **[COLOR=Red]256[/COLOR]**       732558079   2.7 TiB     0700
```

---

### Post by oldfred on 2011-11-20
I would download the newest gdisk if you want to do more than just list partition info with it.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

Both gparted & gdisk seem to say it it ok. Have you copied some data and check to see if you have any issues?

Unless you have real needs for one very large partition, I would not have just one. Since it is NTFS, you need to run chkdsk periodically and it may take days if you fill it with data. Or if you have data corruption any scan tool may take many days to find lost info.

---

### Post by fdrake on 2011-11-20
@oldfred I had the same WD size. I encontered the 4k problem in both situations trying to partition the disk in 1 partition and in multiple partition. Gparted was able to handle ~1tb (better if less ~900MB) of a partition with no problem but i encountered again the 4k problem when partitioning the rest.My solution was to use different fs , I used ext4 , HFS+(no journal)and ext3 . Don't ask me why!

---

### Post by mreos on 2011-11-20
> **oldfred said:**
> I would download the newest gdisk if you want to do more than just list partition info with it.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

Both gparted & gdisk seem to say it it ok. Have you copied some data and check to see if you have any issues?

Unless you have real needs for one very large partition, I would not have just one. Since it is NTFS, you need to run chkdsk periodically and it may take days if you fill it with data. Or if you have data corruption any scan tool may take many days to find lost info.

I accessed the external drive on another ubuntu machine and it seems fine.  At this point, I guess I'll take my chances and assume that **_disk utility_** is just not reporting it correctly.  As you said, gparted and gdisk both says it is ok.  

You mentioned NTFS.  Since my drive is EXT4, will it still take a long time if there is data corruption?

---

### Post by oldfred on 2011-11-20
The ext4 has a faster way of running fsck. But very large partition may still take longer.

---

