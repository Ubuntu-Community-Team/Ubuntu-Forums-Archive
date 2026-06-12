---
title: "My mdadm Raid 6 Server Write Up"
date: 2011-01-09
forum: General Help
---

### Post by TangRedSocks on 2011-01-09
Since I am new to the Unix environment I wanted to document my media-server build so that others can use it as a guideline to bypass all of the pitfalls I seemed to hit. 

This is a three part write up:
1)Ubuntu set-up and Raid share
2)Sharing/Monitoring/Alert(s) of raid
3)Advanced Options

Background:
Over time my media has gone to past the 2TB mark. As such I have been looking into a cheap redundant solution that also has the ability to run handbrake. 

Hardware selection:
Motherboard - Gigabyte EP45 UD3P
Processor - Intel 2 Quad 2.66GHz
Ram - Kingston Hyper X T1 (2x2GB sticks)
Hard Drive(s) - 1 WD Caviar Blue 160 GB 7200RPM
                                                                             [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16822152238"][COLOR=RoyalBlue]6 Samsung F4EG 2TB 5400RPM[/COLOR]
[/URL] 
Initially I set up the server to Win7 and use the ICH10R to run the Intel Rapid Storage Technology to run a raid 5 and share via samba over the network. This turned out to be a bad idea on multiple levels:
* The Intel Rapid Storage Technology program has no notification settings. If you run your server headless you will have no way of getting updated when your volume becomes degraded.  
* Windows 7 smb sharing is slow (they are pushing using homegroup sharing). 
* Administering your server remotely is easily done via [COLOR=RoyalBlue][COLOR=Black]logmein[/COLOR] [/COLOR]applications but if you are on a low bandwidth connection it almost impossible to get anything done.

I decided to go the Ubuntu desktop route. I went standard distribution vs LTS because I plan to keep the OS on a separate hard drive vs the raid so if I have to upgrade down the road no worries. I also did not opt for server because I do not think I would fully utilize all of the options in that package. 

I did not go the FreeNAS route because I decided Raid 6 is a better option for my needs right now. 
I did not go FreeBSD because I assume the support forums at Ubuntu will be more helpful. 
Both of the previous statements are also made because they are the easiest way to ZFS.

Ok so what I did was burn the 10.1 Ubuntu desktop version to disk and installed on my 160 Gig drive. I deleted all of the partitions on the drive and took the manual route as I wanted to add some swap space. From my understanding swap space can be compared to page file in windows systems.  Since I will have more than enough space on the 160 gig drive (cheapest SATA drive I could find around the house) I decided why not give some swap space. So for all of you new to Unix people like me you need to manually set the up the partitions and when you make the partitions use the drop down to make "/swap" partition about twice the size of the physical amount of ram you have in the system and make another "/" partition (known as root) for the rest of the drive space. 

When Ubuntu is set up update it (I plan to do everything through terminal so open terminal up under Accessories->Terminal)
```
sudo apt-get update
```If you buy 2TB drives these days you are going to run into performance issues with misalignment. This is a nice [[COLOR=RoyalBlue]article[/COLOR] ]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=drs-#gpt_solution")explaining it all. The article also shows you how to verify if your drives are aligned using parted:
```
sudo parted /dev/sda 
check-alignment opt
q 
```The issue I had with fdisk is the debate of MBR vs GPT when making a partition table. I wanted to go GPT route so I found the easiest solution was to install Gparted:
```
sudo apt-get install gparted
```This was my first road block per say. Fdisk does not write GPT and Gparted is a GUI. My solution was to remote desktop into the machine and run gparted. I kept the server hooked up to a display, system-> preferences -> remote desktop, set it up how I wanted then went back to my HTPC to further setup the server. 

**Problem 1:** Vino (which is the default remote desktop server application) does not start-up automatically when you boot. So if you are running a headless unit, you can not remote into it. You have to sign in before the server will show up on your remote desktop client. I looked into how to get it to start when I boot the server but have come up empty. Thus I am not 100% headless yet... Vino is all I need so I really do not want to have to setup and install another VNC server. 

Once I got remote working, I used Gparted to set up a partition table (you will have to go to advanced and choose GPT), and then made one partition on each drive aligned to mib with an offset of 1 and unformatted volume. 

Once that was done I went back to parted in terminal to check the alignment of all of the drives and partitions. Everything checked good. 

At this point I now installed and setup SSH. I am not going to cover this because I just followed this:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) (You can not see how much I have relied on Ubuntu forums). My only 2 cents here would be to change your default port. I plan on switching to key based authentication once I get to step three of this project. 

On to mdadm. 
```
sudo apt-get install mdadm
``````
sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=6 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
```Elevate to root:
```
 sudo -s 
```Alter mdadm conf file:
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```Lets make a volume!
```
sudo mkfs.ext4 -c -b 4096 -E stride=32,stripe-width=128 /dev/md0 
```If you are wondering I went with a 128K stripe it is because from what I have read it is a nice option for a large raid 6 array. Lots of other options are available here. The other big debate file system. I was close to btrfs but decided against it because it is still young. You can always convert to btrfs from ext4 on down the road. I did not like slow delete speeds which is why I went with ext4 vs xfs (another popular option).

Now lets test what we got. 
```
sudo hdparm -T -t /dev/sda
/dev/sda
 Timing cached reads:   3404 MB in  2.00 seconds = 1702.49 MB/sec
 Timing buffered disk reads:  382 MB in  3.01 seconds = 126.82 MB/sec
```This is the baseline of what the disk alone is capable of. Raid 6 stripe size is a difficult question to answer as every situation is different. All I want is better than what the disc can do alone on both read and write.

So now let's test my raid setup:
```
sudo hdparm -T -t /dev/md0
/dev/md0:
 Timing cached reads:   3458 MB in  2.00 seconds = 1730.15 MB/sec
 Timing buffered disk reads:  470 MB in  3.00 seconds = 156.52 MB/sec
```Not gonna break any speed records but it is exactly what I was shooting for. Even with GigE, I expect the network to be the bottleneck.

Where my setup is at now:
```
sudo mdadm --query --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jan  7 15:29:35 2011
     Raid Level : raid6
     Array Size : 7814053376 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953513344 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan  9 18:38:21 2011
          State : active, resyncing
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

 Rebuild Status : 47% complete

           UUID : 8fe9e130:be7c000c:2e28bbcb:f6848a15
         Events : 0.9

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
```I think I have done everything correctly so far but I do have one issue I am looking for support on before I move forward:
```
sudo fdisk -l /dev/md0
Disk /dev/md0: 8001.6 GB, 8001590657024 bytes
255 heads, 63 sectors/track, 972804 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      267350  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
```**Problem 2: **The partition 1 line at the end is that cause for concern?


[I]Problems that I need help on:
[/I]**Problem 1: **Vino startup
**Problem 2:** Partition 1 start sector

---

### Post by srs5694 on 2011-01-10
> **TangRedSocks said:**
> The issue I had with fdisk is the debate of MBR vs GPT when making a partition table. I wanted to go GPT route so I found the easiest solution was to install Gparted:

FYI, since it sounds like you might prefer fdisk to libparted-based tools, you might want to look into [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) which is an fdisk workalike I wrote for GPT disks. Note that the version in the Ubuntu repositories is embarrassingly out of date. If you want to use gdisk, please download the latest version from [its Sourceforge downloads page.](http://sourceforge.net/projects/gptfdisk/files/)

> I do have one issue I am looking for support on before I move forward:
```
sudo fdisk -l /dev/md0
Disk /dev/md0: 8001.6 GB, 8001590657024 bytes
255 heads, 63 sectors/track, 972804 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      267350  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
```**Problem 2: **The partition 1 line at the end is that cause for concern?

No. The "partition" shown by fdisk isn't a real partition; it's the protective MBR, which exists just to keep GPT-unaware utilities (like fdisk) from messing with the disk. You need to examine your partition start points using gdisk, GNU Parted, or some other GPT-aware utility, as in:

```

$ **sudo parted /dev/sdb unit s print**
Model: USB Driver (scsi)
Disk /dev/sdb: 15654912s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End        Size       File system  Name                Flags
 1      2048s  10487807s  10485760s  reiserfs     Linux/Windows data

```

...or...

```

$ **sudo gdisk -l /dev/sdb**
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 15654912 sectors, 7.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3C305C6D-0638-4094-90FA-43A14D9362EA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 15654878
Partitions will be aligned on 2048-sector boundaries
Total free space is 5169085 sectors (2.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        10487807   5.0 GiB     0700  Linux/Windows data

```

These examples both show the data from one disk (actually a USB flash drive I use for testing), with a single partition that begins on sector 2048.

---

### Post by TangRedSocks on 2011-01-11
Here is the partition mdadm set up in sectors.:
```
sudo parted /dev/md0p1 unit s print
Model: Unknown (unknown)
Disk /dev/md0p1: 15628103680s
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End           Size          File system  Flags
 1      0s     15628103679s  15628103680s  ext4

```

Loop partition table? I also don't think the fact that I am starting on sector 0 is a problem since I have already verified that all six of the hard drives are aligned after a 1mb offset.
For example all of the drives read this:
```
sudo parted /dev/sda align-check opt 1 print
1 aligned
Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB                     raid

```

Right now I am having trouble with NFS and OSX. Here is the thread: [http://ubuntuforums.org/showthread.php?t=1664387](http://ubuntuforums.org/showthread.php?t=1664387) . I can mount the RAID drive but can not copy and paste in OSX. I can make directories though which is weird. For example if I mount the directory and then terminal to that folder I can "mkdir test" and have the folder be created. But if I go through OSX gui and try to right click or even drag a folder into the mounted volume I do not have permission....

NFS is suppose to be the easy route?

I also retested speeds:
```
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   3648 MB in  2.00 seconds = 1824.83 MB/sec
 Timing buffered disk reads:  378 MB in  3.01 seconds = 125.62 MB/sec

jesse@Blackmamba:~$ sudo hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   3620 MB in  2.00 seconds = 1810.85 MB/sec
 Timing buffered disk reads:  178 MB in  3.03 seconds =  58.73 MB/sec

```

Maybe I will re-stripe...

---

### Post by TangRedSocks on 2011-01-17
[SIZE=5]Part Two:
[SIZE=1]I have not yet got everything I want out of part two but I have made some headway and want to write it down. 

NFS Setup:
Pretty easy setup. I followed this guide: [/SIZE][/SIZE][http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
The only thing here that I had to learn the hard way was folder permissions. What had happened was that I could mount on my OSX machine but could not read/write anything. I looked around and could not figure out what I was doing wrong: [http://ubuntuforums.org/showthread.php?t=1664387](http://ubuntuforums.org/showthread.php?t=1664387). So installed SMB. I took the guesswork out of it because I started to get frustrated. 

How I installed smb:
Right clicked on the RAID folder I mounted the mdadm array to and went to sharing options. Installed the smb packages. Set folder permissions and it worked. Way easier than NFS might I add. 

So then I mounted the SMB on OSX and for giggles I tried to write via the NFS mount. To my surprise both worked with no issues. So I started to look at speed. I have no idea how to log transfer rates, maybe there is some kind of program out there. From just looking at the network transfer on activity monitor I was getting around 2-3mb/sec on the SMB and about 40mb/s on NFS. Wow what a difference.  So I transferred everything I needed to from OSX to the Ubuntu machine. 

Then I went to my windows laptop to try to transfer some items. No issues seeing the SMB. Started to transfer some stuff and again I was only going at 2-3mb/s. Even just 20 gigs of material was going to take quite some time. So I looked around. Found this: [http://ubuntuforums.org/showthread.php?t=342320](http://ubuntuforums.org/showthread.php?t=342320) . Basically add the line to /etc/samba/smb.conf:
```
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```
That pushed it to 4-5mb/s on the transfer after I restarted samaba:
```
 sudo service smbd restart 
```
Nothing I really wanted but it is ok. I just went with it instead of trying to push it any faster. 

[SIZE=3]Monitoring:
[SIZE=1]I went by this guide: [/SIZE][/SIZE][http://basskozz.wordpress.com/2008/12/07/how-to-setup-a-raid5-software-mdadm-array-w-email-notifications-via-gmail-the-easy-way/](http://basskozz.wordpress.com/2008/12/07/how-to-setup-a-raid5-software-mdadm-array-w-email-notifications-via-gmail-the-easy-way/) After reading it I actually went with one of the commenter's suggestions: [http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/).
I am close to this as the email is getting sent but with errors and returned to the inbox of the gmail account I setup specifically for this. Once I get it figured out I will update on the settings I used.

I am also thinking of a list of things I need to attach at the end of this little write-up so that people can basically copy my settings. 
-mdadm.conf
-/etc/exports
-etc



[SIZE=4]Other issues:[/SIZE]
I noticed that I had a hard drive keep removing itself from the raid. Two times I just re-added it to raid by this command:
```
 sudo mdadm --add /dev/md0 /dev/sdf
```Then I would check the rebuild status:
```
 sudo mdadm --detail /dev/md0
```Three time and your out:
Decided to check what the deal was and ran a short test on the drive:
```
sudo smartctl -t short /dev/sdf
```waited some time, had a hard time understanding the results and ran again:
```
sudo smartctl -t short /dev/sdf
```I then took another look at the results and then I could see that the drive is failed:
```
sudo smartctl -l selftest /dev/sdf
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%       702         144259208
# 2  Short offline       Completed: read failure       70%       702         144259168
# 3  Extended offline    Completed without error       00%       416         -

```
I set-up an RMA with Samsung and the drive is in the mail. I put a spare F4EG in the raid so that I can get back to double disk redundancy.  Once the disk comes back I will just convert it to the external enclosure the spare was in before I swapped it in for disk number 6 in my 6 drive raid.

---

### Post by TangRedSocks on 2011-01-18
Hdparm on mdadm raid?
```
sudo hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   3716 MB in  2.00 seconds = 1859.17 MB/sec
 Timing buffered disk reads:  178 MB in  3.02 seconds =  58.99 MB/sec

$ sudo hdparm -Tt /dev/md0p1

/dev/md0p1:
 Timing cached reads:   3606 MB in  2.00 seconds = 1803.38 MB/sec
 Timing buffered disk reads:  404 MB in  3.01 seconds = 134.08 MB/sec

```

If test the sudo drive IE /dev/md0 I get 60mb/s but when I test the partition I get 134mb/s?

---

### Post by v1nny on 2011-01-18
Just a quick note on your hdparm -tT tests: if you're array is still resyncing, which will take a LONG time with 6 2TB drives, you're results are going to suck. Wait until the sync is completed.

> 
sudo mdadm --query --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jan  7 15:29:35 2011
     Raid Level : raid6
     Array Size : 7814053376 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953513344 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan  9 18:38:21 2011
          State : active, resyncing
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0


As to your **Problem 1**, I'd suggest you enable ssh X11 forwarding and use that to bring up GUIs (since you are setting up ssh anyway). I don't know much about using remote displays, but ssh with X11 forwarding works great for most things and typically has lower overhead (if you use compression as well as X11 forwarding, "ssh -XC <host>").

If you're ssh from Windows, you probably need to install cygwin to do X11 forwarding or else use commercial X11 software such as exceed.

---

### Post by TangRedSocks on 2011-01-18
> Just a quick note on your hdparm -tT tests: if you're array is still resyncing, which will take a LONG time with 6 2TB drives, you're results are going to suck. Wait until the sync is completed.

The last hdparm test was done after the sync was done. The re-sync after I put the fresh hard drive in took about 10 hours. 

I will look into X11

---

### Post by srs5694 on 2011-01-18
> **TangRedSocks said:**
> Here is the partition mdadm set up in sectors.:
```
sudo parted /dev/md0p1 unit s print
Model: Unknown (unknown)
Disk /dev/md0p1: 15628103680s
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End           Size          File system  Flags
 1      0s     15628103679s  15628103680s  ext4

```

Actually, that's *not* the partition table setup; that's the contents of *a single partition!* To examine the partition table, you give a device filename for *the entire device*. Normally this is /dev/sda, /dev/sdb, and so on. For software RAID, it would be /dev/md0, /dev/md1, and so on; however, checking on this level is only useful if you partition the software RAID array (which you have); if you use the RAID array directly (putting a filesystem on /dev/md0, for instance), you only need to be concerned with the alignment of the physical drives that make it up.

To summarize:


[list]
[*]Check alignment of partitions on physical drives (/dev/sda, etc.) if you use hardware that requires physical alignment, such as Advanced Format disks, SSDs, or hardware RAID controllers. Details differ from one device to another; but alignment must typically be to some power-of-2 value in kibibytes between 4 KiB and 2048 KiB.
[*]Check alignment of partitions on software RAID devices (/dev/md0, /dev/md1, etc.) if you create partitions within the RAID device. Do this even if the underlying physical devices are properly aligned, since RAID (at least, certain types of RAID, such as 0, 4, 5, and 10) requires alignment to some power-of-2 value (64KiB, 128KiB, 256KiB, or occasionally higher) for optimum performance.
[*]Within individual partitions, proper alignment depends on the filesystem. AFAIK, all modern filesystems align their data structures to reasonable values, so you don't need to worry about in-partition alignment unless you subdivide the partition in some way (nesting partition tables or collecting partitions into RAID devices, as just described).
[/list]

---

### Post by TangRedSocks on 2011-01-21
> Check alignment of partitions on software RAID devices
```
sudo parted /dev/md0 
GNU Parted 2.3
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) align-check opt                                                  
Partition number? 1                                                       
1 aligned
(parted)
```
> Check alignment of partitions on physical drives
```
Using /dev/sda
(parted) align-check opt                                                  
Partition number? 1                                                       
1 aligned
(parted)                                                                  
...(all other drives check good as well) 
```

I still do not understand why hdparm will show a 40mb increase when I test /dev/md0p1 vs /dev/md0...

Other than that I think I have finished up NFS, MDADM, and Email notification which will end this thread.

---

### Post by TangRedSocks on 2011-01-21
**Finished / Part Three:**

For the most part I am finished. I wanted to post my conf files so that others can see exactly what I am running and replicate if all else fails.
My mdadm conf.:
```
DEVICE partitions
ARRAY /dev/md0 level=raid6 num-devices=6 metadata=0.90 UUID=8fe9e130:be7c000c:2e28bbcb:f6848a15

#instruct the monitoring deamon where to send mail alerts
MAILADDR root
PROGRAM /etc/raid_notify.sh

```NOTE: I changed the metadata=00.90 to 0.90 for email complications. I also added my own PROGRAM at the end so that I can get custom updates on raid status. Why? Because the mdadm monitor mode will only email on certain events. It will not for example give you updates on raid re-build progression. I took bits and pieces from these two posts: [http://www.outsidaz.org/blog/2009/11/05/identifying-failed-drives-via-udev-and-mdadm/](http://www.outsidaz.org/blog/2009/11/05/identifying-failed-drives-via-udev-and-mdadm/) and [http://bashukhan.com/tag/customize-default-raid-mdadm-email-template/](http://bashukhan.com/tag/customize-default-raid-mdadm-email-template/) So here is the raid_notify file:
```
#!/bin/bash

#The Event that occurred
MDEVENT=$1

#The md device that is affected
MDDEVICE=$2

#The physical disk that is affected
PHYSDEVICE=$3

#Subject line of the email
SUBJECT="$1 on $2 $3 at $HOSTNAME"

#Logfile for the email
LOGFILE=/tmp/mdadm_logging

echo $SUBJECT > $LOGFILE
echo "******************" >> $LOGFILE
echo "Affected Array  - " $MDDEVICE >> $LOGFILE
echo "******************" >> $LOGFILE
echo "Detail of current action being done" >> $LOGFILE
cat /proc/mdstat >> $LOGFILE
echo "******************" >> $LOGFILE 

#Check to see if the physical disk parameter ($3) has been passed. If it is not
#null then mdadm has passed it, and we can check the disk via udev.
if [ -n "$PHYSDEVICE" ];
        then
                echo "Affected Physical Drive  - " $PHYSDEVICE >> $LOGFILE
                echo "******************" >> $LOGFILE
                echo "Physical Drive Information is as follows " >> $LOGFILE
                echo "******************" >> $LOGFILE
                udevadm info --query=all --name=$PHYSDEVICE >> $LOGFILE
fi
mail -s "$SUBJECT" root < $LOGFILE
/bin/rm $LOGFILE

```With that in place I manually failed and removed a drive from the raid, then added it back, and waited for it to re-sync. I did this 4 times since I first built the raid. I am now very confident that if something happened I would be able to jump in and save my data. Here is what my email came up with:
[IMG]http://i.imgur.com/Cr4Dl.png[/IMG]

My ssmtp conf:
```

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=*********@gmail.com

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.gmail.com:587

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=*********@gmail.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

UseSTARTTLS=YES
UseTLS=YES
AuthUser=*********@gmail.com
AuthPass=******

```Now here is my /etc/exports:
```

# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/RAID/RAID 192.168.0.0/24(rw,insecure,no_root_squash,async,no_subtree_check)

```And here is how I mounted on OSX:
[IMG]http://i.imgur.com/AzBbm.png[/IMG]
then...
[IMG]http://i.imgur.com/1h9d0.png[/IMG] 

From there I saw transfer rates like this:
[IMG]http://i.imgur.com/vpwxi.png[/IMG]

This is what really makes me happy as transferring at the 3-4mb/s range was unbearable. I average about 70mb/s on a write.

I plan to look more into smartctl email notifications and apcupsd email notifications. I will try to remember to post on this thread when I have that all set up and going. 

Overall I am really happy with the results vs my old Win7 setup with Intel Rapid Storage taking care of raid. If I left out anything let me know and I will post it up.

---

### Post by psusi on 2011-01-21
A few points:

1)  As someone else mentioned, wait until the resync is finished before testing the performance

2)  If you don't want the gui, then don't use the gui frontend to parted (gparted); use parted directly.

3)  Recent versions of parted take care of the alignment automatically

4)  The default block size is already 4096 bytes, so you don't need to specify it explicitly to mke2fs

5)  I am pretty sure that mke2fs will auto detect the stripe factor if you don't explicitly specify it

6)  Why did you partition the array?  I suggest you do not do this.  Fdisk complains about it because as you already noted, it does not support GPT, which you used to partition the array.

---

### Post by srs5694 on 2011-01-21
> **TangRedSocks said:**
> ```
sudo parted /dev/md0 
GNU Parted 2.3
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) align-check opt
```

One caution: The [http://www.gnu.org/software/parted/manual/html_node/align_002dcheck.htmldocumentation for parted]() says that the "align-check" feature check for proper partition alignment against "the disk's selected alignment criteria," but it's unclear what the criteria actually are in your case.

Instead of relying on parted to get it right (which is risky at best, between uncertainty about what the "alignment criteria" might be and parted's history of bugs), I recommend displaying the partition start points to sector accuracy and seeing if they're divisible by whatever value is required for your configuration. (If they're divisible by 2048, you're fine for any modern media, and some can use much lower values -- 512, 8, or even 1, which of course requires no checking.)

Given your performance improvements, I'd say the odds are that everything's now fine with your current setup. I did want to get this caveat in the thread for your own future reference and any other readers, though.

---

### Post by psusi on 2011-01-21
> **srs5694 said:**
> One caution: The [http://www.gnu.org/software/parted/manual/html_node/align_002dcheck.htmldocumentation for parted]() says that the "align-check" feature check for proper partition alignment against "the disk's selected alignment criteria," but it's unclear what the criteria actually are in your case.

It is based on what the drive reports its optimal alignment to be.  So far, I don't think any drives have started reporting that, so it defaults to 1 MB.

---

### Post by TangRedSocks on 2011-01-24
> **psusi said:**
> A few points:

1)  As someone else mentioned, wait until the resync is finished before testing the performance

2)  If you don't want the gui, then don't use the gui frontend to parted (gparted); use parted directly.

3)  Recent versions of parted take care of the alignment automatically

4)  The default block size is already 4096 bytes, so you don't need to specify it explicitly to mke2fs

5)  I am pretty sure that mke2fs will auto detect the stripe factor if you don't explicitly specify it

6)  Why did you partition the array?  I suggest you do not do this.  Fdisk complains about it because as you already noted, it does not support GPT, which you used to partition the array.

1) Results are after rysnc was done.
2) I used parted cli to check drive alignments
3) That is what I assumed. The drive(s) have a 1mb offset from what I can tell
4) Ok
5) Ok
6) I am confused on this. How do you write data to a raid volume with no partition. Again I am just recently converting over form the Windows frame of mind. 

> Instead of relying on parted to get it right (which is risky at best, between uncertainty about what the "alignment criteria" might be and parted's history of bugs), I recommend displaying the partition start points to sector accuracy and seeing if they're divisible by whatever value is required for your configuration. (If they're divisible by 2048, you're fine for any modern media, and some can use much lower values -- 512, 8, or even 1, which of course requires no checking.)See my answer #3 above.

I took another step forward. I got the server to email on a raid failure but what about a system shutdown?

I made a little startup/shutdown script:
```

#!/bin/bash

#Set date
CDATE=`date`

#Set Raid Status
SRAID=`cat /proc/mdstat`

option="${1}"

case ${option} in 

start)
ssmtp  -oi whereitisgoing@gmail.com << EOF
From: Blackmamba <serveremail@gmail.com> 
To: whereitisgoing@gmail.com
Subject: Blackmamba is ONLINE @ $CDATE

Blackmamba is online, hide the women and children.

System startup was executed at $CDATE

**********************
Current RAID status is:

$SRAID
EOF
;;

stop)
ssmtp  -oi whereitisgoing@gmail.com << EOF
From: Blackmamba <serveremail@gmail.com> 
To: whereitisgoing@gmail.com
Subject: Blackmamba is OFFLINE @ $CDATE

Blackmamba is going offline. 

System shutdown was executed at $CDATE

**********************
Current RAID status is:

$SRAID
EOF
;;
esac

```Save that in /etc/init.d
then change permissions to allow execution:
```
 sudo chmod +x server_email 
```then add it to run the start part when the server starts up and the stop part when the server shuts down:
```
sudo update-rc.d -f server_email defaults 
```I needed to restart the server so that it could update. 
```
 sudo shutdown -r now
```and then look what we have here:
[IMG]http://i.imgur.com/sY2DN.png[/IMG]

Man this is really coming along.

---

### Post by psusi on 2011-01-24
> **TangRedSocks said:**
> 
6) I am confused on this. How do you write data to a raid volume with no partition. Again I am just recently converting over form the Windows frame of mind. 

The same way you write to any block device.  The fact that hard disks are usually subdivided into partitions that are each assigned a block device is just convention; it isn't necessary.  MD devices originally did not have partition tables and were just used directly ( /dev/md0 ).  These days they can be partitioned, but the old ways work best.  Keep it simple.

---

### Post by TangRedSocks on 2011-01-24
Since my data is already on the drive pool I do not think I am able to switch to a partitionless setup. The other thing that I wonder is why the partition writes so much faster: 
```

$ sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   3694 MB in  2.00 seconds = 1847.70 MB/sec
 Timing buffered disk reads:  190 MB in  3.03 seconds =  62.74 MB/sec
$ sudo hdparm -tT /dev/md0p1

/dev/md0p1:
 Timing cached reads:   3688 MB in  2.00 seconds = 1845.22 MB/sec
 Timing buffered disk reads:  386 MB in  3.03 seconds = 127.27 MB/sec

$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jan  7 15:29:35 2011
     Raid Level : raid6
     Array Size : 7814053376 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953513344 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan 24 14:40:32 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

           UUID : 8fe9e130:be7c000c:2e28bbcb:f6848a15
         Events : 0.8448

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1

```

---

