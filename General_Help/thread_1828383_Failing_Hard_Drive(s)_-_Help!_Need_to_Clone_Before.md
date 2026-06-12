---
title: "Failing Hard Drive(s) - Help! Need to Clone Before Drive Fails Completely"
date: 2011-08-18
forum: General Help
---

### Post by Do0d on 2011-08-18
Hello and thanks for taking a moment to read about my dilemma. 

About two years ago my friend and I built my linux work station as I wanted to do away with windows completely (yay!). My friend had many years of experience using linux, and I was a novice. 

I decided to opt for a raid system, with a small fast HD (74 GB Western Digital raptor) to hold my OS, and two 1 TB WD in raid 1 mode to hold my data on. 

We also performed what I believe he called a sym-link, to move my home folder to the raid, so if I had a failure, even my desktop and home folder would be on the raid. 

All good in theory, and it probably has saved my data now that two of the three drives are suffering bad sectors. At this time it takes about 20 minutes for my system to boot, upon startup the system attempts to check the disks & filesystem, but fails and says there is no /tmp file or its busy. I then get take to a screen that asks me if I was to skip, ignore, or manually repair. The only option that doesn't cause a reboot is ignore. After about 5 mins my login screen appears, then I can get into my desktop but all apps are seriously slow to load and there is constant freezing. Also, the system boots in read only mode, and I cannot run fsck or seemingly get anywhere while in read only mode.

I dont know if cloning a drive that is this messed up is a good idea and I'm concerned my unusual setup will give me fits when I attempt to clone the drive with clonezilla. Should I proceed with cloning the 74 GB OS drive? Do I need to clone the Raid as well or can I unhook the raid, and hook up the new 150GB drive I have to replace the 74 GB failing drive? (clonezilla docs are unclear on whether or not the new HD needs to be attached to the system to copy the image while the old drive is being cloned)

Obviously I'm slightly confused after doing days and days of reading on this. I just need some up to date information, this data is my life, I run my business from this machine, so I cant take any risks, hence the Raid setup. I'm running 10.04 64 bit, but currently logged in through the live CD. I attempted to run badblocks, or fsck (sudo fsck -pcfv /dev/sda), but I am getting a file system mounted or opened exclusively by another program? I attempt umount /dev/sda terminal says umount: /dev/sda is not mounted (according to mtab)


Please help before I lose the rest of my marbles...er data!

---

### Post by Do0d on 2011-08-19
Ok, I hooked up my new hard drive 150GB and disconnected the raid and attempted to run clonezilla. I got through the prompts and warnings, to about 70% of the clone, and then clonezilla crashed with /opt/drb1/sbin/ocs-onthefly: line 893:  3340 aborted   partclone. Failed to clone /dev/sda1 to dev/sdb1!!! press enter to continue........

When I press enter nothing happens, its seems clonezilla is frozen?

Any help or other clone programs I should try would be greatly appreciated!

---

### Post by Ozymandias_117 on 2011-08-19
> **Do0d said:**
> I attempted to run badblocks, or fsck (sudo fsck -pcfv /dev/sda), but I am getting a file system mounted or opened exclusively by another program? I attempt umount /dev/sda terminal says umount: /dev/sda is not mounted (according to mtab)

You can use ```
mount
``` to see what filesystems are mounted.  The reason you're having problems is because you're trying to unmount /dev/sda instead of /dev/sda1 (Or whatever partition number is mounted)

---

### Post by Do0d on 2011-08-19
None of the HD should be mounted when I boot through the Live CD tho correct? 

Im running Gparted at the moment (or I would boot into live and check to be certain), but it too is failing when I attempt to copy and paste partitions to the new drive. I'm getting input output drive error from sda. 

I guess my next step is ddrescue, although Im a little unclear of how to use ddrescue seeing as I cant install it from the repository. ubuntu starts in read only mode (updates all fail so I assume installing anything from synaptic will as well). 

Any ideas on what I should be attempting to do here? I just moved and dont know anyone around that knows anything about ubuntu or linux. 

Any help you can provide would be fantastic!

---

### Post by Hakunka-Matata on 2011-08-19
can you take a screenshot of gparted's graphic, and post it?

you may have a swap file on sda that is mounted, the liveCD might be using it, but it can be safely unmounted.

---

### Post by Do0d on 2011-08-19
Ok, I was able to run fsck and complete on /dev/sda1, but on the larger part of the drive dev/sda3 when running fsck I got an unexpected error and fsck told me to run fsck manually without the -p or -a options. The 74 GB drive has 1217 bad sectors, so I need to get this data off of it fast, if it isnt already too late.

Below is the screen shot in gparted. I guess my next attempt is to boot with clonezilla & run /sbin/ddrescue /dev/sda /dev/sdb logfile in terminal, unless you guys have another idea on what I should try next.

[IMG]http://www.freeimagehosting.net/9bb23[/IMG]

[IMG]http://www.freeimagehosting.net/9bb23[/IMG]

[[img]http://www.freeimagehosting.net/t/9bb23.jpg[/img]](http://www.freeimagehosting.net/9bb23)

---

### Post by Wim Sturkenboom on 2011-08-19
Why are you cloning your OS disk? Which data is on there that is important? Wouldn't it make more sense to make a backup of the data on the raid?

---

### Post by Do0d on 2011-08-19
I have some pretty hacked up stuff on the OS disk, an eclipse install that I wouldnt know how to reinstall with all the tweaks done over the last two years, plus, we made some sort of sym-link putting my home folder on my raid drive somehow. I have no idea how to replicate that process as a friend did it for me when I built the machine 2 years ago. 

I was going to replace the failing raid drive next once the system is stable. Of you have other suggestions, believe me I am all ears.

---

### Post by Duncan Williams on 2011-08-19
You will need to read right through this site re/ the free backup software. It used to do full backups of windows, linux and dual boot systems.
[http://www.todo-backup.com/products/home/](http://www.todo-backup.com/products/home/)

You may be able to use it to backup your failing hard-drive.

---

### Post by Do0d on 2011-08-19
Ever get the feeling the universe is plotting against you? 

I started ddrescue early this morning about the time of my last post (11 hours). 

To do this I booted from the live CD, installed gddrescue from synaptic, opened terminal and ran ddrescue as so: sudo /sbin/ddrescue /dev/sda /dev/sdb logfile. I watched for awhile as the errors added up, but the data seemed to be moving along so I opted for some sleep, until I was woken by utter silence follwed by a loud crack of lightening outside. 

Yes, you guessed it, the power went out during my ddrescue attempt. I rebooted from the live CD, and back to terminal, and fired up ddrescue once again, expecting it to start recovery from wherever it stopped according to the logfile. Upon starting ddrescue the initial status is listed as 0B rescued 0B error size and 0 errors. 

Is my logfile not working because I lost power running via live CD? I was under the impression the logfile was being saved on the destination drive? I'm looking now to see where the logfile is saved, the documentation however is no easy read.

UPDATE

I misunderstood the logfile portion of the command. 

Im trying ddrescue again with sudo ddrescue -n /dev/sda /dev/sdb rescue.log to rescue all free blocks, then taking another pass when that is finished with sudo ddrescue -r 1 /dev/sda /dev/sdb rescue.log

I canceled ddrescue and restarted, and sure enough it picked up where it left off, so I know the logfile is working now. Hopefully I can now rescue my data and then on to the failing raid drive.

---

### Post by Do0d on 2011-08-22
ddrsecue was successful, recovering all but 5kb of my data. I am able to boot up properly, but I am still having issues updating. I thought the failure to update had something to do with the bad drive, but I am still getting the same error when I attempt an update. 

here is the error update is giving me:

Reading database....60%dpkg: unrecoverable fatal error, aborting:
files list file for package 'liborbit2' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover


nothing happens at this point, it just says update complete. I've found a couple references from 2008 for liborbit2, but im worried that information could be out of date.

Anyone have any ideas here? I'm almost back in business, if I could update that would be huge!

Update:

I started a new thread on this issue since it's not related to the failing hard drive: [http://ubuntuforums.org/showthread.php?p=11175218#post11175218](http://ubuntuforums.org/showthread.php?p=11175218#post11175218)

---

