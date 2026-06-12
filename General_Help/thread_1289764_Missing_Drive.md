---
title: "Missing Drive"
date: 2009-10-12
forum: General Help
---

### Post by BrutalSpoon on 2009-10-12
Hi Guys,

A bit of background context:

I have an NTFS SATA drive which I use as my Windows 7 system drive. A few days ago my computer decided to turn itself off as Windows was shutting down (thats an issue for another time). I didn't think much about it (after all, it's done it before and coped fine) until I went to restart - it gets past the BIOS but doesn't even begin to boot Windows due to some error or other.

So, being used to reinstalling Windows for various reasons, I went to boot up my Kubuntu partition but the hard drive has been starting to fail for a while now and I think it's finally killed itself.

-----------------------------------

To cut a long story short, I dug out an old 40GB IDE drive and managed to get it working with gOS (which as you probably all know is based on Ubuntu). And here lies my problem:

My Windows 7 drive shows up in gOS as a SCSI disk. When I double click on it in the file browser to mount it, I get the error "Unable to mount location: Can't mount file". It doesn't even show up in GParted (although I can see where it's supposed to be) - GParted shows drives sda, sdc and sdd.

Using the command fdisk /dev/sdb returns "Unable to open /dev/sdb", and using sudo fdisk /dev/sdb returns "Unable to read /dev/sdb". Using cat /etc/fstab gives the following:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5806d88d-68cc-41c8-b478-02937b7603fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d7e99145-cc59-4832-9996-f2f710a48c92 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


And using sudo fdisk -l returns the following:

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcef2284c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4701    37760751   83  Linux
/dev/sda2            4702        4865     1317330    5  Extended
/dev/sda5            4702        4865     1317298+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121602   976762583+  ee  EFI GPT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x815a524f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60802   488383488    7  HPFS/NTFS


Still no mention of sdb.

I just want to grab the files off my W7 disk so that I can nuke it and reinstall it. Any suggestions?

Thanks in advance,
BrutalSpoon

---

### Post by cwbar_1 on 2009-10-12
Do you have a Windows 7 or Vista disc?  I so, boot using disc, and choose "Repair."  If the hard drive is OK, you should be able to recover.

---

### Post by BrutalSpoon on 2009-10-13
> **cwbar_1 said:**
> Do you have a Windows 7 or Vista disc?  I so, boot using disc, and choose "Repair."  If the hard drive is OK, you should be able to recover.

Sorry, I should have given you more information - I have the W7 disc but it's apparently unable to repair it. All my restore points have conveniently disappeared, too. It appears my only option is to grab the files that I need and to format the drive, in which case I need to be able to mount it in gOS, which is why I've come to the ubuntu forums for help.

Thanks for the suggestion, but it doesn't really help me - is there anything else you could suggest?

---

### Post by mechro on 2009-10-13
I would try Puppy Linux. If that doesn't mount and read your drive you'll probably need a data recovery tool like testdisk.

---

### Post by BrutalSpoon on 2009-10-13
> **mechro said:**
> I would try Puppy Linux. If that doesn't mount and read your drive you'll probably need a data recovery tool like testdisk.

I'll give it a try, but what makes Puppy Linux different to other distributions? :confused:

---

### Post by P4man on 2009-10-13
if "sudo fdisk -l" doesnt show it, nothing will be able to retrieve any info off it afaics. It probably doesnt even show up in your bios, or does it?

Id suggest checking the bios for sata options (like disabling raid). If that doesnt help,  opening your case, and checking cables, or connect the drive to a different sata header.

---

### Post by BrutalSpoon on 2009-10-13
> **P4man said:**
> if "sudo fdisk -l" doesnt show it, nothing will be able to retrieve any info off it afaics. It probably doesnt even show up in your bios, or does it?

Id suggest checking the bios for sata options (like disabling raid). If that doesnt help,  opening your case, and checking cables, or connect the drive to a different sata header.

Yes, it does show up in the BIOS. My motherboard for some reason displays all my hard drives as IDE devices (although 3 of the 4 which are connected are SATA drives), but all four of them show up in the BIOS. I put it down to the motherboard being one of the cheapest you could get with integrated graphics at the time (and therefore low quality) but that could just be me being naïve and not knowing what I'm talking about :rolleyes:

I'll give Puppy Linux a go, then turn to testdisk if that doesn't work I suppose.

Thanks everyone for your help so far, I appreciate it :)

---

### Post by live2learn on 2009-10-13
Its seems the /dev/sdd1 * 1 60802 488383488 7 HPFS/NTFS is the sdb drive your looking for. try this command below
"sudo mount -t ntfs-3g /dev/sdd1 /media/disk" in the terminal.
make sure the folder /media/disk exist.

---

### Post by BrutalSpoon on 2009-10-13
> **live2learn said:**
> Its seems the /dev/sdd1 * 1 60802 488383488 7 HPFS/NTFS is the sdb drive your looking for. try this command below
"sudo mount -t ntfs-3g /dev/sdd1 /media/disk" in the terminal.
make sure the folder /media/disk exist.
Unfortunately sdd is not the hard drive I'm looking for. I have 4 hard drives in my current set up:

- A 40GB IDE drive which I'm using to run gOS (sda)
- A 320GB SATA drive which I use to run W7 (sdb and the drive I'm trying to recover)
- A 1TB SATA drive (sdc)
- A 500GB SATA drive (sdd)

---

### Post by mechro on 2009-10-13
> **BrutalSpoon said:**
> I'll give it a try, but what makes Puppy Linux different to other distributions? :confused:

It works for me. There's less complications with file permissions, it'll just copy stuff till the cows come home. I wouldn't use it as a working desktop, that's obviously Ubuntu's job!

---

### Post by arrange on 2009-10-13
Does *dmesg* say anything about the drive?```
dmesg | egrep 'scsi|sdb|SCSI|ata'
```

---

### Post by BrutalSpoon on 2009-10-13
> **mechro said:**
> It works for me. There's less complications with file permissions, it'll just copy stuff till the cows come home. I wouldn't use it as a working desktop, that's obviously Ubuntu's job!

Ah, I see what you mean. I just booted off a Live CD and made some progress!

Its mount utility didn't do anything for me, but when I started up GParted it actually acknowledged that the drive was there, which was a start. It even allowed me to do a scan and it showed up the one partition with an error. On asking for information I got this:

> **Warning:**

pread: Input/output error
Failed to calculate number of free clusters: Input/output error
Failed to mount 'dev/sdb1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was made to NTFS by this software.


ntfsresize v2.0.0 (libntfs 10:0:0)
Error reading bootsector: Input/output error
Failed to startup volume: Input/output error
ERROR(5): Opening 'dev/sdb1' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was and will be made to NTFS by this software until it gets repaired.


Unable to read the contents of this file system!
Because of this some operations may be unavailable.

What do you make of that? Unfortunately I no longer HAVE a version of Windows to run chkdsk on (unless you can do that using the install DVD like you can use disk utility on an OS X install DVD)

---

### Post by P4man on 2009-10-13
its just saying it won't mount the ntfs volume because its "dirty", ie, it wasnt properly closed down. To retrieve files from it, you could try force mounting it manually as read only. not sure about the exact syntax, but google should tell you.

---

### Post by BrutalSpoon on 2009-10-13
> **P4man said:**
> its just saying it won't mount the ntfs volume because its "dirty", ie, it wasnt properly closed down. To retrieve files from it, you could try force mounting it manually as read only. not sure about the exact syntax, but google should tell you.

Well, I tried force mounting it without much success, so I'll try starting up with the windows disk again and try to run chkdsk on it (although I couldn't find it last time :confused:) And see if that helps at all.

If it weren't for a few games, Windows Live Messenger (which I prefer in general to pidgin), Chrome and a few other applications I'd be very sorely tempted to just format it and stick ubuntu on it. Either way I still have to get my data off it first, though.

I'd like to thank everyone once more for their help - it's gotten me a lot closer to solving things than I'd ever get on my own!

---

### Post by mechro on 2009-10-14
> **BrutalSpoon said:**
> Well, I tried force mounting it without much success, so I'll try starting up with the windows disk again and try to run chkdsk on it (although I couldn't find it last time :confused:) And see if that helps at all.


Perhaps chkdsk is Startup Repair on the disk... mentioned here...

[http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7)

---

### Post by BrutalSpoon on 2009-10-15
> **mechro said:**
> Perhaps chkdsk is Startup Repair on the disk... mentioned here...

[http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7)

Unfortunately not - that just checks for the files that Windows uses to boot, and I wasn't even able to get that far with the drive.

**--- Start TL;DR section here - Read at your own peril! ---**

I did manage to get somewhere with the drive yesterday, though. I took it to a friend's place and he stuck it in an eSATA enclosure. We managed to get it recognised in Windows and it ran a quick chkdsk. When I got back home, I plugged it in and tried booting in to windows just on the offchance that it'd work - it did! It took 3 times longer than usual, and when I was finally able to log in I wasn't able to use it for very long - turns out C:/Program Files/Common Files was corrupted as well as some other files vital to the system, making it pretty unstable, but it was actually working.

As an aside, I wasn't able to hear it in my case but in the eSATA enclosure a clicking was clearly audible while the drive was doing a sequential read - this disk is on its way out. I'd been suspicious about this for a while but I don't really have the money to replace it, so I've been hoping that it'd be okay.

Fom this I was able to discover the disk using the W7 install disc, which allowed me to run chkdsk /f /r. It took all night, and it froze when scanning the last of the free clusters, but it was progress.

I was then able to actually force mount the disk and browse through it temporarily in puppy linux, although it managed to virtually kill the instance I'd booted off the Live-CD, let alone let me mount any of my other disks to copy over the files I needed. This disk is seriously messed up!

I'm now on a Linux-Mint Live-CD, but as of yet it's still unable to mount the bad disk. I'm going to boot off the W7 install DVD and run chkdsk again, but with only the /f parameter this time. It SHOULD be much quicker and do enough for me to force mount it in Linux-Mint so that I can grab the files I need. Safe to say I won't be using this drive for much afterwards, let alone as a system drive!

Luckily my friend happens to have freed up a 200gb disk of his from one of his backup systems and hopefully will be able to give it to me today.

Of course, none of this would have been overly problematic if I'd been smart enough to run backups - although most of my data is spread over my other disks and I try to keep only applications and system files on my system drive, there is still some data which is used by the applications themselves that has to be on the system drive. Nothing stopping me from backing it up, though!

This has spurred on my next project - a DIY NAS based on a mini-ITX PC which runs (almost) silently and contains 2 internal and 2 external drives - 2 for backups and 2 for data.

**--- End TL;DR section here ---**

I'd just like to thank everybody once more for all their ideas and help getting this sorted out. A gold star for each of you! :KS

Without your help I'd still be wondering how the hell I'd ever be able to get at my data. I really appreciate it :)

---

### Post by mechro on 2009-10-17
If you have trouble getting the drive to work when backing up to your new drive, you could always try the freezer trick...

[http://www.emergingtechs.com/posts/put-your-hard-drive-in-the-freezer-to-recover-data/](http://www.emergingtechs.com/posts/put-your-hard-drive-in-the-freezer-to-recover-data/)

---

