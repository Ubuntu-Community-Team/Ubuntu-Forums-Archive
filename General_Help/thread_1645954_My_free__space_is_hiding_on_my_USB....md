---
title: "My free  space is hiding on my USB..."
date: 2010-12-15
forum: General Help
---

### Post by .knic34 on 2010-12-15
[FONT=Verdana]Hello all,

I'm having some issues with my install of Ubuntu 10.10 onto a 8GB usb stick.  I have completed the install and everything seems to be working perfectly booted on my Dell, except I am unable to see most of the free space on the drive...under "Places:Computer" I click the properties on the File System drive and it shows only 656MB of free space...

I made the mistake of forgetting to partition the drive before install; am I out of luck now? should I reformat, partition, and then install again? or is there extra space hiding somewhere I cant find? (I'm somewhat new to Ubuntu, so I'm not familiar with all the nooks and crannys yet!)

Thanks everyone!
[/FONT]

---

### Post by zeroseven0183 on 2010-12-15
Open System Monitor in System > Administration and go to File Systems tab. There you can view the status of your partitions. Check if that 656 MB is the same with what you see in System Monitor.

---

### Post by theDaveTheRave on 2010-12-15
> **.knic34 said:**
> [FONT=Verdana]Hello all,

I'm having some issues with my install of Ubuntu 10.10 onto a 8GB usb stick. 

So you are running ubuntu directly from your usb stick (a bit like running a 'live' CD. I've never personally done this, so I may be incorrect in some of my advice... that said, the commands should give you some assistance in finding a solution (if only by elimination).

> 
 I have completed the install and everything seems to be working perfectly booted on my Dell, except I am unable to see most of the free space on the drive...under "Places:Computer" I click the properties on the File System drive and it shows only 656MB of free space...

What about the other disks that are on the computer, does it see them, and correctly show how much used / free space there is??



> 
I made the mistake of forgetting to partition the drive before install; am I out of luck now? should I reformat, partition, and then install again? or is there extra space hiding somewhere I cant find? (I'm somewhat new to Ubuntu, so I'm not familiar with all the nooks and crannys yet!)

Thanks everyone!
[/FONT]

Ok for starters, you could try the following... I've done them in my terminal and included my output (coloured) for information...

```

df -h
[COLOR="Lime"]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              24G   16G  6.8G  70% /
none                  240M  324K  240M   1% /dev
none                  244M  572K  244M   1% /dev/shm
none                  244M  296K  244M   1% /var/run
none                  244M     0  244M   0% /var/lock
none                  244M     0  244M   0% /lib/init/rw
/dev/sda5              33G   27G  5.9G  83% /home
/dev/sda9              14G   13G  1.8G  88% /usr/local[/COLOR]

```

here you can see the 'partitions' that the system has currently mounted.

next you will want to see if the details of the disks is the same in the device section.

the first set of results is without a USB key inserted
```

ls /dev/disk/by-path -l
[COLOR="Lime"]total 0
lrwxrwxrwx 1 root root  9 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 2010-12-15 14:14 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../sr0[/COLOR]

```

and when I put a USB key in....
```

ls /dev/disk/by-path -l
[COLOR="Lime"]total 0
lrwxrwxrwx 1 root root  9 2010-12-15 15:16 pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-12-15 15:16 pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 2010-12-15 14:14 pci-0000:00:1f.2-scsi-0:0:0:0-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 2010-12-15 14:14 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../sr0[/COLOR]

```

So now the extra stuff that hasn't been 'mounted' can at least be seen as being detected. You may also want to use < ls /dev/disk/by-label -l > check the output of < ls /dev/disk > for the other output formats, that may be useful to you (us) in troubleshooting the problem.

check this thread [how to mount a usb stick]("http://ubuntuforums.org/showthread.php?t=1484052&highlight=mount+usb+key+CLI") for instructions to do this.

Just as a matter of interest what is the file manager you are using? I know that nautilus normally shows up 'unmounted' partitions, but I'm not sure of the others.

Any problems, post the results of your commands here.

David

---

### Post by .knic34 on 2010-12-17
Yes, under Computer I am able to see the two partitions of my 160GB internal hard drive with my windows install and my mics files (they seem to be showing correct free/used space information), I am able to see my CD/DVD drive, and I am able to see a "1.1GB File: casper-rw" (not familiar with that), in addition to my "File System" drive.

Under my terminal I get the following output:


"df -h"     
-----------------------:
Filesystem            Size  Used Avail Use% Mounted on
aufs                  896M  195M  651M  24% /
none                  997M  252K  997M   1% /dev
/dev/sdb1             7.6G  1.7G  5.9G  23% /cdrom
/dev/loop0            661M  661M     0 100% /rofs
none                 1003M  112K 1003M   1% /dev/shm
tmpfs                1003M   12K 1003M   1% /tmp
none                 1003M   88K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock


"ls /dev/disk/by-path -l"      
 -----------------------:
total 0
lrwxrwxrwx 1 root root  9 2010-12-17 05:02 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-12-17 05:02 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-12-17 05:02 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-12-17 05:02 pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-12-17 05:02 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-12-17 05:02 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2010-12-17 05:02 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../sr0


Another observation I had: whenever I click on the USB drive in my Disk Utility program, I see that the "Drive" device says /dev/sdb and the "Volume" device says /dev/sdb1, with the Mount Point set at /cdrom....whenever I view the "File System/cdrom" folder, I see that it has 5.6 GiB of free space!  could it be mis-named because I am booting directly from the USB (ie, as a liveCD)?? 

 However now when I go to try and add something to this folder, it informs me that I am not the owner and I do not have permissions...this could be why the free space is not showing?  Is there any way I can be instructed on how to reset the permissions?

As far as what File Manager I am using, I am not sure (Default file manager for GNOME: ubuntu 10.10)

Thank you again, everyone, for all your help!

---

### Post by cipherboy_loc on 2010-12-17
What is the output of:

```
sudo fdisk -l
```
and
```
mount
```

From what it looks like, you have a live-usb install (live-cd + casper-rw), not a real Ubuntu install. From df -h, it looks like you have a small (800MB) file mounted as /, but I cannot understand how you can only have 200MB used; it must be a live-usb...  I cannot get my Ubuntu (with X and Fluxbox) under 1.79GB, so with disk usage of 200MB, there must be something else. What did you use to install to the USB key? 





Cipherboy

---

### Post by dcstar on 2010-12-17
> **cipherboy_loc said:**
> What is the output of:
........
**From what it looks like, you have a live-usb install** (live-cd + casper-rw), not a real Ubuntu install. From df -h, it looks like you have a small (800MB) file mounted as /, but I cannot understand how you can only have 200MB used; it must be a live-usb...  I cannot get my Ubuntu (with X and Fluxbox) under 1.79GB, so with disk usage of 200MB, there must be something else.

**Exactly.**

You are asked to set aside the R/W space on the USB when you create it, if you do not specify enough then you don't get to use it.

Putting the USB in another system will probably show heaps of free space on it waiting for a new partition to be created.

This doesn't really matter anyway, a Live USB device is a poor substitute for a real install and the Casper-RW area will fill up quite quickly because **you can never recover deleted space** from that type of filesystem.

---

### Post by oldfred on 2010-12-18
Since you have a 8GB flash drive you can do a full install not a standard USB install that is just for installing. Even with persistence you can only store so much data and cannot do updates. Note that any install to USB flash will be slower both due to USB speeds and flash speeds (especially writing).

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

You do have to be sure to install grub to the MBR of the flash drive. It will normally default to the sda drive. With Maverick you only get the choice of where to install if you use manual install.

See post by C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by theDaveTheRave on 2010-12-20
So this is what I understand from the info you have posted....


> **.knic34 said:**
> 

"ls /dev/disk/by-path -l"      
 -----------------------:
total 0
lrwxrwxrwx 1 root root  9 2010-12-17 05:02 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0 -> ../../[COLOR="SeaGreen"]sdb[/COLOR]
lrwxrwxrwx 1 root root 10 2010-12-17 05:02 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1 -> ../../[COLOR="Lime"]sdb1[/COLOR]



Tells me that the USB drive is partioned into 2 partitions, sdb and sdb1 (coloured)

> 
"df -h"     
-----------------------:
Filesystem            Size  Used Avail Use% Mounted on
aufs                  896M  195M  651M  24% /
none                  997M  252K  997M   1% /dev
/dev/sdb1             7.6G  1.7G  5.9G  23% /cdrom



This suggests that sdb is your root (the aufs line) folder, and /dev/sdb1 contains a the subpartition, that for some reason is mounted at /cdrom ??

So if you open nautilus (or your file browser) you should be able to access the rest of your disk from the /cdrom directory.

I'm not sure what problem you will have with it mounted there in terms of read / write permisions.

Also put a CD into the true CD drive of your pc to see where it is mounted (my guess is it will be filesystem /dev/cdrom, mounted at /cdrom2 or similar).

Remember you may need to mount the filesystem to see it.

David

---

### Post by .knic34 on 2010-12-21
UPDATES:

 I have decided to scrap this install, make sure I PARTITION this time! and then do a full installation instead of a live-USB install, see if that will make it run a bit better.

also, FYI, for those of you who were curious, for this initial install I used PenDriveLinux, which (if I understand it correctly) just created a USB version of the live-CD ISO (hence the /cdrom)

Thank you again to everybody for your help!

---

### Post by QLee on 2010-12-21
[QUOTE=.knic34]...
 I have decided to scrap this install, make sure I PARTITION this time! and then do a full installation instead of a live-USB install, see if that will make it run a bit better.
...[/QUOTE]

Next time you want to look at partitions from the live CD version, use the program GParted. It might also be a good idea to install it on your real install.

You had only 1 partition on your stick, sdb1, sdb is the stick itself.

Take note of oldfred's advice in post 7, "Note that any install to USB flash will be slower both due to USB speeds and flash speeds (especially writing).", that will be a limiting factor for system performance as compared to internal drive speed. Flash(in this case it means, stick) speeds will vary somewhat directly proportional to cost of the stick.

---

### Post by theDaveTheRave on 2010-12-21
If you are going to install from a source CD, and you are feeling upto it then I would recomend the alternate installer.

Particularly if you are installing on a desktop.

Why?? Because it has better handling of disks available to it, for instance, if you partition your main HDD with a root, home etc etc this is great, but when you realise you didn't have enough space you and you decide to extend and disk (or parition) onto a new disk, with the standard installer, you can't.

Although this may have changed in recent versions.

Also if you are feeling brave, I would recomend installing the 'server' version (again I think it is an alternate install by default). This way you end up with a smaller footprint on your disk, downside is of course you will then most likely need to manually update to get all the nice software that you need. I however find this inconvenience to not be an inconvenience (ifyou get my drift)

Anyway good luck, and remember to put your experiences on the [Poll: What is your Maverick Meerkat install/upgrade experience]("http://ubuntuforums.org/showthread.php?t=1595311") thread.

David

---

