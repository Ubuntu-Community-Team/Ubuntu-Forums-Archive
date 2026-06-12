---
title: "External hard drive busy, can't format"
date: 2010-10-12
forum: General Help
---

### Post by brent.yerkish on 2010-10-12
Hello, all!  

I apologize in advance if this has been covered, but I can't find an answer for this here or elsewhere.  

I recently installed Ubuntu on my laptop with no problems...until now.  I bought a Seagate portable drive for backup/extra storage purposes.  When I plug in the drive and start up Disk Utility, it recognizes the Drive and whatnot, but when I click "Format Drive" I end up (after clicking through the warnings) with an error message stating:

[I][B]Error Formatting Drive
[/B]
An error occurred while performing an operation on "640 GB Hard Disk" (Seagate Portable):  The device is busy

[/I]I clicked for details, which resulted in:

*One or more partitions are busy on /dev/sdb*

(Not that detailed, if you ask me.)

I then entered the command line (a scary place for someone who came over from OSX).  

```
sudo lshw -C disk
```[FONT=Arial]

gave me this info about the hard drive I'm trying to format:

[/FONT]```
 *-disk
       description: SCSI Disk
       product: Portable
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdb
       version: 0130
       serial: 2GH308NB
       size: 596GiB (640GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=0305033c
```[FONT=Arial]

I tried running:

[/FONT]```
sudo fdisk /dev/sdb
```[FONT=Arial]

That went swimmingly until I pressed "w" to write, as you can see below:

[/FONT]```
****************@*****:~$ sudo fdisk /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): c
DOS Compatibility flag is not set

Command (m for help): u
Changing display/entry units to sectors

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
1 heads, 63 sectors/track, 19845456 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0305033c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1250263727   625130840   83  Linux

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (2048-1250263727, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-1250263727, default 1250263727): 
Using default value 1250263727

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
```It seems to be a slightly more detailed version of the error from Disk Utility.  

Does anybody have any ideas what I'm doing wrong?  Or perhaps what command I can use to figure out exactly what the device is doing?  Maybe a selective "kill" command for all processes using a specific piece of hardware?  

Thanks in advance for your help!  

Brent

---

### Post by CharlesA on 2010-10-12
Try this please:

```
sudo lsof /dev/sdb
```

---

### Post by brent.yerkish on 2010-10-13
Thanks for the speedy reply.  


```
**********@****:~$ sudo lsof /dev/sdb
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/**********/.gvfs
      Output information may be incomplete.

```Not sure what that means...*(does a quick google search or seven)*

Someone on the internet says using -w will suppress that warning, so:

```
 **********@*****:~$ sudo lsof -w /dev/sdb
```...well that resulted in nothing...nada...gave me a fresh command prompt.

---

### Post by CharlesA on 2010-10-13
Try a reboot and go from there.

---

### Post by brent.yerkish on 2010-10-13
I tried a couple reboots already, both with the external disk attached and unattached...but here goes...

Huh.  That worked like a charm...if you have the time, would you mind explaining why for my own edification?  

If not, a thousand thanks for your help.

---

### Post by CharlesA on 2010-10-13
I'm not sure, but normally the lsof would show you what process was using the drive. It mentioned .gvfs, which can't be read or written to by anyone but your user, so I figured try a reboot.

The reboot caused whatever was using the drive to terminiate, so you can work with it again.

This is what it said for one of my drives (that is running Samba):
```
charles@thor:~$ sudo lsof /dev/sdb1
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF      NODE NAME
smbd    18915 root  cwd    DIR   8,17     4096 165543937 /array/charles
```

---

### Post by brent.yerkish on 2010-10-13
Thanks!

---

### Post by Prince_Peculiar on 2011-06-30
I have this same issue... Maybe I'm a complete idiot, but do you mean just a reboot of the computer? If so, I have restarted my computer umteen times in the last month and STILL have this issue.

---

### Post by starrtennis on 2012-09-18
lsof followed by a reboot did not work for me.

Model: WD WDC WD20EARS-00MVWB0, 2.0 TB

it's on /dev/sdb and I get the same error message as op.

-Mike

---

### Post by overdrank on 2012-09-18
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

