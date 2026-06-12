---
title: "File system check damaged Ext4 with GParted LiveCD, is it recoverable?"
date: 2011-11-07
forum: General Help
---

### Post by CPUNeck on 2011-11-07
I was victimized by the HP tx2500 Pavilion GPU fiasco, and finally bought a new laptop, but not before the HP got numerous opportunities to just SLAM the file system shut.  The drive was taken from the HP and mounted via the USB on my new laptop.  All was well, seemed everything was there, but then I opened a few .jpg files and noticed there was some corruption to the pictures (pixelated, cut off, incomplete, etc.) So I figured the drive needed to be checked.

Fired up GParted, ensured drive was not mounted, and clicked "check."  Well little did I know how long this button click would take.  I viewed the msg log and saw errors (can't recall now)  Google pointed me to the USB connection and its power as the source of the errors.  I had to choose to continue with the errors, or cancel.  I canceled, mounted in new laptop, booted with GParted LiveCD and again selected check.  It ran for ~30 hours before I canceled to relocate the drive into a computer I could do with out for the next few weeks if it took that long.  

The first time I canceled from the USB and installed into the computer, I noticed the reported used space was like 7GiB, when it should have been closer to 90GiB.  All partitions were properly reported, only the used portion was wrong, reporting MOST of my data when way of the bit bucket.  When I placed it in the long term machine (dual drives), I mounted it using Nautilus, came up no problem, but only had 4-5 folders and a lost+found.

My question is 1) have I lost any information?  Nothing has been written to the drive other than the utilities.  Does canceling the "check" operation corrupt data?  It's been unmounted for all operations.  The file system is Ext4 from Ubuntu 11.04.  The size is 320GiB.  The live GParted CD is an older tool, but I now am using the fsck -y utility on Ubuntu 11.10 in vtty-1.  I've read and read on inode tables, superblocks and still have no clear route to restore the drive to it's original state.  Right now the vtt-1 is deluged with "Clone multiply-claimed blocks"

It seems the drive is completely fubar, and all I wanted to do is "clean" it so my files were complete.  The OS didn't complain about the file system.  I'm still new so ignorance is bliss ](*,)  Sorry for the long post, needed to get all the info out.

---

### Post by dcstar on 2011-11-08
> **CPUNeck said:**
> 
.........
My question is 1) have I lost any information?  Nothing has been written to the drive other than the utilities.  Does cancelling the "check" operation corrupt data? 


[LIST=1]
[*]Probably.
[*]It is "Check and Repair", you interrupt it when it is writing and you **will** corrupt the partition.
[/LIST]

---

### Post by matt_symes on 2011-11-08
Hi

I'm afraid dcstar sounds right here. Sounds like the filing system is fubared.

I would check in the lost+found folder though. Depending on what fsck found, it can put files into lost+found directory. That is what the lost+found directory is for.

In future i would make a clone of the drive using dd - assuming no bad blocks - or ddrescue and then run fsck on that image.

That way you don't touch the original hard drive and it gives you more attempts to fix the image.

Then you can run a whole bunch of attempts such as using a different superblock or recreating the journal file.

Kind regards

---

### Post by CPUNeck on 2011-11-08
Well there ya go.  Lesson learned.  I was aware of the .img options (dd, ddrescue) and also of the time and space resources required for it.  I didn't know the GParted "check and repair" utility was unable to be canceled (cleanly stop).  After learning more about the file-system, it would appear the utility could use a type of journal for itself and maintain it's progress for future operations.

It's still running, and will until it's complete.  Is there some damage control I could institute?  If the partition structure is mucked up, could I recover it from a secondary table on the drive?  I tried to understand the metadata structure, but still don't have a handle on it.  Looks like the superblock describes the drive, file-system, and geometry.  The inode tables geographically map data to files names.  Perhaps a program to parse the inode tables? :confused: I know, drawing straws... thanks for the help.

---

### Post by matt_symes on 2011-11-08
Hi

Let it run until it has finished then you can see where you are.

 > If the partition structure is mucked up, could I recover it from a secondary table on the drive?

The partition table ? No, unless you have backed it up.

The partition table is a different beast than the filing system in a partition and you are having problems with the filing system by the sounds of it.

Wait until it has finished and then you can see the state of the filing system.

Did you check the drives SMART status (it it has that capability) ?

Kind regards

---

### Post by CPUNeck on 2011-11-08
I will check the S.M.A.R.T. status upon the fsck's completion.  This drive was not exhibiting any issues.  The problem arose from the HP laptop over heating, and seizing.  I'd have to do hard rests on it, and I'm sure the file system was left dirty.  Thanks for the help, I'll hope for the best, and report the results.

---

### Post by CPUNeck on 2011-11-13
Ok, so this is ridiculous... the drive is still running, and not hung.  Meaning I can see activity from the conky drive information area, seeing access' to the drive.

I know HD's are not predictable, but this drive is less than six months old and is a WD 320.  Prior to me monkeying with it there were no errors, other than the noticed .jpg file problem when mounted to a different computer.  I can not find any log file being generated by the fsck.ext4 program.

My laptop has two SATA ports, both with identical drives. sda is the boot and mounted, sdb is the busted one, not mounted.  I have not done any work on this drive while mounted.  Is this what I can look forward to if my drive is shut down "dirty"?  I hope not.

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000788de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   608401407   304199680   83  Linux
/dev/sda2       608403454   625141759     8369153    5  Extended
/dev/sda5       608403456   625141759     8369152   82  Linux swap / Solaris

[COLOR="Red"]Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000792e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   602898431   301448192   83  Linux
/dev/sdb2       602900478   625141759    11120641    5  Extended
/dev/sdb5       602900480   625141759    11120640   82  Linux swap / Solaris[/COLOR]
```

```
Last login: Sun Nov 13 13:39:23 2011 from cpu-dl6420.teamss
cpuneck@catsi1-dv7:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   13216 MB in  2.00 seconds = 6612.80 MB/sec
 Timing buffered disk reads: 330 MB in  3.01 seconds = 109.68 MB/sec
cpuneck@catsi1-dv7:~$ sudo hdparm /dev/sdb

/dev/sdb:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0
cpuneck@catsi1-dv7:~$ iostat -x
Linux 3.0.0-12-generic (catsi1-dv7) 	11/13/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          12.51    0.01    0.15    0.37    0.00   86.96

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.11     0.75    0.46    1.10     8.80    58.21    85.68     0.07   41.90   22.87   49.81  13.03   2.04
sdb              14.34     6.05    0.54    0.07    59.50    24.51   274.76     0.00    3.49    3.00    7.05   2.17   0.13

```

Here you can see how long it's been running!
```
cpuneck@catsi1-dv7:/var/log/fsck$ top

top - 14:23:30 up 6 days,  8:07,  2 users,  load average: 1.00, 1.01, 1.05
Tasks: 201 total,   2 running, 199 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.7%us,  0.1%sy,  0.0%ni, 85.8%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4038236k total,  3679756k used,   358480k free,  1011568k buffers
Swap:  8369148k total,   168300k used,  8200848k free,   918444k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
15869 root      20   0  711m 556m  640 R  100 14.1   8488:08 fsck.ext4          
28416 root      20   0  432m 120m  84m S    1  3.1  23:16.79 Xorg               
  942 messageb  20   0 26144 2848 1020 S    0  0.1  16:10.61 dbus-daemon        
 1372 root      20   0 95224 5380 1660 S    0  0.1   8:22.02 python             
28630 mama      20   0  615m  96m  35m S    0  2.5  17:45.36 compiz             
28907 mama      20   0  606m 167m 3316 S    0  4.2  18:19.61 conky              
    1 root      20   0 24176 1716  912 S    0  0.0   0:02.25 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.08 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:01.87 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   33 root      20   0     0    0    0 S    0  0.0   0:00.61 sync_supers        
   34 root      20   0     0    0    0 S    0  0.0   0:00.01 bdi-default        
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd        
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd
```

It's running under Ctrl-Alt-F1 (tty1), and I didn't pipe the output, so I can remotely view the contents of the screen, but can switch to it and view the screen.  All I've gotten past the very initial stuff was:

File...(inode # xxxxx, mod time .....) has 491,055 multiply-claimed block(s) shared with 7 files: <filesystem metadata> and lists the files.

That was just an example entry, there are many other entries with a smaller multiply-claimed value, but I've seen at least two this large.  How could the drive get this screwed up?  More importantly my confidence I'll get ANYTHING off this drive is waining.  If I loose everything, I'll be a "black eye", but not just me for not backing up, but Ubuntu gets one too, for years I worked on FAT and NTFS and never came across anything like this.  Thanks for the help in advance. ](*,)

---

### Post by Cyclane on 2011-11-13
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
> First you copy as much data as possible, without retrying or splitting sectors:

ddrescue --no-split /dev/hda1 imagefile logfile 
Now let it retry previous errors 3 times, using uncached reads:

ddrescue --direct --max-retries=3 /dev/hda1 imagefile logfile 
If that fails you can try again but retrimmed, so it tries to reread full sectors:

ddrescue --direct --retrim --max-retries=3 /dev/hda1 imagefile logfile 

I recommend you try this.

---

### Post by Mark Phelps on 2011-11-14
Sorry to tell you this ... but the quality of recent WD drives is not what it used to be.

I had a 1TB WD "Green" drive fail on me -- and it was less than a year old.  Downloaded and ran the WD utility (in Windows) -- an even IT failed to recover the drive. Got less than 15% into the drive and hung up -- time after time.

Replaced that with a Seagate drive -- and haven't had any problems since.

---

