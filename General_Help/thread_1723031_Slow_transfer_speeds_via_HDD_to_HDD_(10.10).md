---
title: "Slow transfer speeds via HDD to HDD (10.10)"
date: 2011-04-06
forum: General Help
---

### Post by Dr_Frost on 2011-04-06
I have read many threads but cannot find a solution on this:

First, All HDD & SSD benchmark just fine (DISK UTILITY):
ALL SATA
Vertex 30 GB - AVG READ = 114MB/sec | MIN/MAX = 60/193
SAMSUNG 2.0TB - AVG READ = 78MB/sec | MIN/MAX = 30/120
SEAGATE 1.5TB - AVG READ = 104MB/sec | MIN/MAX = 60/135

Now no matter how i transfer if its from HDD to HDD or to SSD i never get more then 18-20MB/sec, i just tried booting to my live CD and was able to transfer with 24-25MB/sec

This is really slow, since the worst (2.0TB) can do a minimum of 30 READ

Anybody got any ideas, this seems to be something that has plagued ubuntu for years, and no i don't want to try other distros, i tried almost all of them a year ago and finally went with ubuntu

---

### Post by Dr_Frost on 2011-04-07
bump, this is an ignoring bug......

---

### Post by antaios256 on 2011-04-07
i know the type of file system can directly effect the read and write speeds.

```

sudo fdisk -l

```and post the output of the drives and partition types
(example below)
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        7342    58762479+   7  HPFS/NTFS
/dev/sda3           60789       60802      105496    c  W95 FAT32 (LBA)
/dev/sda4            7342       60789   429312001    5  Extended
/dev/sda5            7342       58620   411894784   83  Linux
/dev/sda6           58620       60789    17416192   82  Linux swap / Solaris

```

---

### Post by Dr_Frost on 2011-04-07
```
Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eec3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3769    30273437+  83  Linux
/dev/sda2            3770        3893      991233    5  Extended
/dev/sda5            3770        3893      991232   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdde9c08b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa379c585

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS

------------------------------------Short List------------------------

/dev/sda1   *           1        3769    30273437+  83  Linux
/dev/sda2            3770        3893      991233    5  Extended
/dev/sda5            3770        3893      991232   82  Linux swap / Solaris

/dev/sdb1               1      266306  2147483647+  ee  GPT

/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS

```

Again every drive runs fast in it self, boot is very fast on the SSD, but when transferring between disks/ssd speed will never go over 20MB/sec

---

### Post by srs5694 on 2011-04-07
First, as antaios256 mentioned, filesystems have overhead, and that could be slowing things down. Thus, if you've got a raw read rate of 30 MB/s, by the time you add in filesystem overhead and the need to juggle both input and output, getting 20 MB/s might be perfectly plausible.

Second, some modern disks have special alignment requirements, as described in [url=http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/]an article I wrote[/quote] for IBM developerWorks. I recommend you check on this. You can do so by typing:

```

sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print
sudo parted /dev/sdc unit s print

```

Check the start sector of each partition. If it's divisible by 8 for an Advanced Format disk, it's fine. SSDs have alignment issues, too, but I'm less familiar with precisely what they are. Many modern tools align partitions on 2048-sector (1-KiB) boundaries, which works well with (AFAIK) all modern disks.

---

### Post by Dr_Frost on 2011-04-07
sorry to be lazy here but it's 2 o clock at night so im just going to post the output

```

[B]sudo parted /dev/sda unit s print
[/B]Model: ATA OCZ-VERTEX (scsi)
Disk /dev/sda: 62533296s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End        Size       Type      File system     Flags
 1      2048s      60548922s  60546875s  primary   ext4            boot
 2      60549118s  62531583s  1982466s   extended
 5      60549120s  62531583s  1982464s   logical   linux-swap(v1)

[B]sudo parted /dev/sdb unit s print
[/B]Model: ATA SAMSUNG HD203WI (scsi)
Disk /dev/sdb: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start    End          Size         File system  Name                          Flags
 1      34s      262177s      262144s                   Microsoft reserved partition  msftres
 2      264192s  3907028991s  3906764800s  ntfs         Basic data partition

[B]sudo parted /dev/sdc unit s print
[/B]Model: ATA ST31500341AS (scsi)
Disk /dev/sdc: 2930277168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      63s    2930272064s  2930272002s  primary  ntfs

```

What do i have to do to make this better?, i am getting a new 2TB HDD in the next week so i have to do a backup first before i make changes to the disks.....
Well let me refraise that, lets say i get 2 new 2TB disks how do i need to format them
And also a new Vertex II 60GB, again formatting this to.
And i presume that it will be best to format all in EXT4, i don't really have the use for NTFS anyway, no MS here anymore

Sorry to be so helpless, i just want this set up ones and for all, + a good help to others that experience low transfer speeds.

Really hope this will fix the speed thing, it is seriously the last thing i need fixed for a perfect system, everything else is just super :)

---

### Post by nerdy_kid on 2011-04-07
ok this might be a really stupid question, you're not using wubi right?

---

### Post by Dr_Frost on 2011-04-07
don't know what wubi is but looking at software center i find:
ibus-table-wubi  **(NOT INSTALLED)**
ibus-table [B](INSTALLED)

[/B]is this what you mean???

---

### Post by nerdy_kid on 2011-04-07
no -- when you installed Ubuntu, did you install it from the CD (i.e. boot off the CD) or did you install it inside Windows (i.e. have windows running, pop the disc in and run wubi.exe).

---

### Post by srs5694 on 2011-04-07
> **Dr_Frost said:**
> sorry to be lazy here but it's 2 o clock at night so im just going to post the output

What do i have to do to make this better?

Your /dev/sda and /dev/sdb are properly aligned for all modern drives, but /dev/sdc is not. That might or might not be a problem; it depends on what type of drive it is. To figure that out, *you* need to do some research. Find out what the requirements are for *your* hardware.

---

### Post by Dr_Frost on 2011-04-07
Oh that wubi, no my process is installing from USB or MINI-DVD for my own custom Frost 10.10 (remastersys), so no win involvement there

And heres the kicker for the 1.5TB & 2.0TB, they where formatted in Win before i really started with different linux distros.

And apparently win is not good at formating very logically, not to mention the stupid 100MB part on the 2.0TB, Damm i really hate win.... kicking myself every day that i didn't go to linux sooner, i first saw it in 99 and was amazed, but im a creature of habit like most and maybe hooping win will finaly work probably, but after spending time with 7 i just finally got my sh*t together... (side track i know)

Back to the case in hand.
Is my best bet here to get all the new HDD/SDD's and format all in EXT4 and get all the partitions in line with the divide with 8?

---

### Post by Dr_Frost on 2011-04-07
> **srs5694 said:**
> Your /dev/sda and /dev/sdb are properly aligned for all modern drives, but /dev/sdc is not. That might or might not be a problem; it depends on what type of drive it is. To figure that out, *you* need to do some research. Find out what the requirements are for *your* hardware.

Testing again: (1.4GB file)
Transfer from sda to sdb = 15MB/sec (**BAD**)
Transfer from sdb to sda = 27MB/sec (**OK**)
Transfer from sda to sdc = 23MB/sec (**OK**)
Transfer from sdc to sda = 18MB/sec (**BAD + LAGGING**)
Transfer from sdb to sdc = 21MB/sec (**OK**)
Transfer from sdc to sdb = 14MB/sec (**BAD**)

I might rate them as **OK** but it is not **GREAT!!**
In the win days it was faster then this, and this is the only thing im missing

---

### Post by Dr_Frost on 2011-04-09
Just got my Vertex 2 60GB, and transferring from Vertex to Vertex 2 (both EXT4) gives a transfer speed of 75MB/sec, so this could really the problem, with the divide by 8 and EXT4 of course also helps

Im getting a new 2TB disk in less then a week, will update when it is formatted to EXT4 and i can begin transferring everything from my 2TB disk, and then formatting it probably and then do some transfer tests.

---

### Post by antaios256 on 2011-04-09
i just wanted to thank the people who stepped up to help the original posted i started to troubleshoot and got busy with school :P

---

### Post by Dr_Frost on 2011-04-11
Ok got the 2TB disk today, and formatted it to Ext4, now transferring can be done with 75MB/sec :)
And thats about minimum now.

I have not looked at any alignment, have only formatted to Ext4

Damm nice to have some decent transfer speeds again

---

### Post by Dr_Frost on 2011-04-12
Status update: have 2x 2TB disks & 1x 60GB SSD all running EXT4, have not looked at any alignment.
Transfer Speeds are now minimum 75MB/sec


Problem Solved from here by formatting ALL disks to EXT4.

---

