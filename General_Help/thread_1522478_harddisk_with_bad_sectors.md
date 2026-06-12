---
title: "harddisk with bad sectors"
date: 2010-07-02
forum: General Help
---

### Post by camel_33 on 2010-07-02
Dear forum,

After days of trying hard to rescue my unreadable hard disk (and of course reading your forum :) I finally signed up as I couldn't find (or implement the right) solution by myself. Let me describe the problem (symptoms), and then outline what I have already done:

When starting up my OS last week (Ubuntu 9.10) there were lots of error messages and a clicking (ticking) sound. Later I read on the forum that this probably due to a bad sectors or even a dying hard disk. After another attempt I realized it wouldn't be a good idea to keep trying mounting (writing to) the hard disk.

So I quickly decided it would make sense to buy a new HD (just in case) but also a USB to IDE/ATA adapter in order to copy the damaged HD to the new (external) HD. For this purpose I used the 10.04 live CD, carefully avoiding mounting the damaged HD inside my laptop.

When I open GParted I see:

- dev/sda1 (ext4) Size 35gb, of which 23gb used and 13gb unused (this is the partition with bad sectors and all important files I'd like to copy)
- dev/sda2 (sda5/6 extended) Size 39gb, of which 34gb unused (this partition can be mounted, but has no important files)
- unallocated (at the very end) 200 MB

Now I have already installed and tried GNU ddrescue with Synaptic Package Manager but without success. But before I carry on with that, I'm now thinking that since I have space left on the internal HD (dev/sda2, see above), perhaps it's not necessary to copy the files to the external drive (which btw has a capacity of 160gb). That means I would have to resize, move and/or copy with GParted, or wouldn't that work when dev/sda1 has bad sectors?

All comments highly appreciated :)

Rgds, camel

---

### Post by s.v.z on 2010-07-02
Hi and welcome to the forum.

I assume you`d better make an image of your entire bad hdd (or the first partition only, if you wish ) on your external hdd and experiment with it to make sure you don`t damage the data while attempting to recover it. Unfortunately, I`m quite new to linux, so I can`t advise any recovery programs. R-Studio was great under Win. 

Maybe some of these will help
[http://www.thefreecountry.com/utilities/backupandimage.shtml](http://www.thefreecountry.com/utilities/backupandimage.shtml)
[http://www.r-tt.com/data_recovery_linux/](http://www.r-tt.com/data_recovery_linux/)

P.S. the clicking sound when the hdd starts means you`re having trouble with the hdd heads. It`s gonna die. Just a matter of time.

---

### Post by camel_33 on 2010-07-02
Hi, many thanks for yr reply.

Your 2 links look very promising, I'll take a closer look at them later.
Re. making an image: I've already tried what with ddrescue but without success.
To begin with, the external (target) HD which I connected via the USB to IDE/ATA adapter to where I would copy the damaged partition is not recognized. At least not when I type sudo fdisk -l in Gnome Terminal. It is however recognized in Sys/Adm/DiskUtility as 'sdb'.

---

### Post by john newbuntu on 2010-07-02
I concur with s.v.z. that you need to back up your partition/data to another disk as soon as you hear those clicking sounds for the first time.  These are signs of HDD's demise sooner or later.  

Once you clone the image, you could try photorec or other tools given in the article below to recover as much as you can from the cloned drive:
[http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd](http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd) 

If you can not, there are professional HDD data recovery experts out there who could rip open your drive and, for instance replace the heads/actuator/logic board or other components and re-image the drive for you once they get it to work.  Of course all this involves cost.

Going forward, please do remember to image your partitions or the drive periodically.  Might save you a hell a lot of nightmares.

---

### Post by camel_33 on 2010-07-02
Hi, I fully agree with imaging (copying the partition to another HD asap) but that's just the problem.. 
I've tried that with GNU ddrescue but without success.. 
When I type 'sudo ddrescue /dev/sda1 /dev/sdb' the error message is: 'write error: No space left on device'
Anyway, I'm afraid I can't stay here much longer as I gotta go see Holland play Brazil this afternoon.
Be back soon..

---

### Post by warfacegod on 2010-07-02
sda2 is a separate partition on the the drive that sda1 resides on. If that HDD (hard drive) is failing, especially with the clicking sounds, moving your files to another part of the HDD won't matter. You'll still probably lose that data.

Here is what I recommend. Trans fer your personal data to your new HDD and then use it to replace the failing one in your computer. Boot into a Live Environment with the CD and go to: System> Admin.> Gparted.

Your going to want to create two new partitions for sdb, your new HDD. You may need to unmount it first. The first should be around 10 -15 GB and the second should be the rest of the drive. Both should be formatted as ext4 and both should be primary partitions. Apply your changes. Make sure you new HDD is mounted again.


Now you'll want to move all of your stuff to the biggest partition. Hit Alt+F2 and enter gksudo nautilus. Use that to navigate to your old HDD's home folder. Not the /root home. It should be filesystem/home/username. Drag n" Drop the username folder (I assume that's camel or something.) and the other username folders, if any, into the big partition you just created.

Post back once your done.

---

### Post by camel_33 on 2010-07-04
Hi sorry for late reply, I didn't have internet over the weekend or only via mobile phone.
Thanks for all replies, but the 1st step remains unsolved: copying/transferring sda1 to the new HDD. I've tried this using ddrescue but without success. The target HDD is not recognized. I'm using a USB to PATA adapter.

---

### Post by warfacegod on 2010-07-04
Are you doing this from a LiveCD of Ubuntu?

---

### Post by camel_33 on 2010-07-04
yes I am. Although right now replying from my mobile phone as I just come home from the weekend spent outdoors. 
So yes, when attempting to copy to the external HDD (using ddrescue) it was always from the live CD (10.04), with the damaged HDD inside the laptop.

---

### Post by camel_33 on 2010-07-04
PS: over here it's almost midnight but I'm gladly willing to carry on this thread as I'm starting to believe rescue is close. So do let me know if this time (in yr part of the world) is convenient to you and I'll switch on the laptop (via the live CD). If not we'll (hopefully :) continue later.

---

### Post by warfacegod on 2010-07-04
Let's just skip ddrescue for the moment and see if simple Drag n' Drop works. Boot into Live with new HDD plugged in and on, via USB. Then Alt+F2> "gksudo nautilus" (no quotes). From therenavigate to the /home folder and see if you can drag it into your new HDD.

---

### Post by camel_33 on 2010-07-05
OK, I'm finally back online at full internetspeed with the laptop (damaged HDD inside), running from Ubuntu live CD 10.04 and new external HDD connected via USB. I just did as you suggested, i.e. opened gksudo nautilus. However all I see there is:

- root
- desktop
- filesystem
- network
- trash

but no /home folder

Also, the external HDD connected via USB is not there. neither in GParted, but only in Sys/Admin/Disk Utility as dev/sdb.

---

### Post by warfacegod on 2010-07-05
If Disk Utility is seeing it then try to mount it from there.

Looks like your using the lefthand pane to look for /home, so click /filesystemand /home should be listed there.

---

### Post by camel_33 on 2010-07-05
There is no such option to mount, all I can do from DiskUtility is 'format drive' or 'format volume'. I should also mention that the drive appears to be 'not partitioned'. 

Re.gksudo nautilus:
Under 'filesystem/home' the next (sub)folder is 'Ubuntu' and all the rest seems to me it belongs to the Ubuntu live CD.

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> There is no such option to mount, all I can do from DiskUtility is 'format drive' or 'format volume'. I should also mention that the drive appears to be 'not partitioned'. 

Re.gksudo nautilus:
Under 'filesystem/home' the next (sub)folder is 'Ubuntu' and all the rest seems to me it belongs to the Ubuntu live CD.

My fault, I forgot it was LiveCD. filsystem> media> find the correct drive (should be a string of numbers)> /home

Post a screenshot of Disk Utility with the external highlighted. It sounds like it doesn't have a filesystem.

---

### Post by camel_33 on 2010-07-05
nope, under filesystem/media there's only the USB flash drive (memory stick).

> **warfacegod said:**
> My fault, I forgot it was LiveCD. filsystem> media> find the correct drive (should be a string of numbers)> /home

sorry, not sure how to make a screenshot :confused:

Post a screenshot of Disk Utility with the external highlighted. It sounds like it doesn't have a filesystem.

---

### Post by warfacegod on 2010-07-05
Easiest way to make a screenshot is to hit the PrintScreen button. Mine is called PrtSc.

Is your internal listed in Places? If so, click it. Then /home.

---

### Post by camel_33 on 2010-07-05
pls find attached the screenshot

---

### Post by wynand2020 on 2010-07-05
Hi

Why dont you download clonezilla, make a image backup of your system, then buy a new harddrive and restore the image. Good as new!

---

### Post by camel_33 on 2010-07-05
OK thanks for the instructions :) I just uploaded.
Re. my internal HDD, that's just the issue: due to 'a few bad sectors' (according to DiskUtility) it's impossible to mount dev/sda, i.e. certainly isn't listed under 'Places' in the filebrowser nor gksudo nautilus.

---

### Post by warfacegod on 2010-07-05
Okay, that gives us lots of information.

.01 We now know that your internal *is* being seen. I presume its the Toshiba drive.

.02 Your new drive is empty and has no filesystem. I've never actually seen a drive come that way but I've heard of it. Normally it would have been formatted as NTFS. This is also why ddrescue wasn't seeing the drive.

You're going to need to format the new drive. If you aren't going to be using it with Windows then ext4 is the probably best to use. Be absolutely certain you have the proper drive selected in the left hand pane. After that is done, mount the volume. The icon will be in the upper left corner of Disk Utility.

Now if your old drive isn't in the Places menu, mount it with Disk Utility while your there.

---

### Post by camel_33 on 2010-07-05
Hi, yes I was also considering Clonezilla, but we're first trying to resolve the USB to IDE/ATA connection. 
I already bought and connected a new HDD but can't 'see' it. Before we move to cloning, we need to establish a working connection.

> **wynand2020 said:**
> Hi

Why dont you download clonezilla, make a image backup of your system, then buy a new harddrive and restore the image. Good as new!

---

### Post by camel_33 on 2010-07-05
Hi Warfaceofgod, I do believe there's still hope now.
I took note of yr last post, but let me first post another screenshot, of the internal HDD (from DiskUtility).

---

### Post by camel_33 on 2010-07-05
oeps, that had to be in a 'full' reply.
So here's the screenshot.

---

### Post by warfacegod on 2010-07-05
Ignore the previous comment about the mount icon in the upper left. I'd forgotten that Palimpset (Disk Utility) has had  makeover.

Anyway, what happens when you click the Mount Volume button?

---

### Post by camel_33 on 2010-07-05
.01 We now know that your internal *is* being seen. I presume its the Toshiba drive.

that's right

.02 Your new drive is empty and has no filesystem. I've never actually seen a drive come that way but I've heard of it. Normally it would have been formatted as NTFS. This is also why ddrescue wasn't seeing the drive.

I had installed Ubuntu 10.04 from the live-CD on that HDD, but backed up the few files I created there. When I attempted ddrescue it looks like it erased the whole disk. But that's OK.

You're going to need to format the new drive. If you aren't going to be using it with Windows then ext4 is the probably best to use. Be absolutely certain you have the proper drive selected in the left hand pane. After that is done, mount the volume. The icon will be in the upper left corner of Disk Utility.

OK, so my next move will be 'format drive' (i.e. the new HDD connected via USB) from Disk Utility.

Now if your old drive isn't in the Places menu, mount it with Disk Utility while your there.[/QUOTE]

Sorry, but I'm a bit confused here. I thought I should never mount a HDD with bad sectors. Wouldn't that further damage the HDD?

---

### Post by camel_33 on 2010-07-05
When I click 'format drive' I get the following options:
- Master boot record
- GUID partition table
- Don't partition
- Apple partition

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> .01 We now know that your internal *is* being seen. I presume its the Toshiba drive.

that's right

.02 Your new drive is empty and has no filesystem. I've never actually seen a drive come that way but I've heard of it. Normally it would have been formatted as NTFS. This is also why ddrescue wasn't seeing the drive.

I had installed Ubuntu 10.04 from the live-CD on that HDD, but backed up the few files I created there. When I attempted ddrescue it looks like it erased the whole disk. But that's OK.

You're going to need to format the new drive. If you aren't going to be using it with Windows then ext4 is the probably best to use. Be absolutely certain you have the proper drive selected in the left hand pane. After that is done, mount the volume. The icon will be in the upper left corner of Disk Utility.

OK, so my next move will be 'format drive' (i.e. the new HDD connected via USB) from Disk Utility.

Now if your old drive isn't in the Places menu, mount it with Disk Utility while your there.

Sorry, but I'm a bit confused here. I thought I should never mount a HDD with bad sectors. Wouldn't that further damage the HDD?[/QUOTE]

That explains why there was no filesystem on it.

Yes it could but you'll have to mount it at some point to be able to read it's contents. I don't think anything can read it, be it ddrescue, clonezilla, or whatever, without the drive mounted. But don't worry about mounting it just yet. Let's just concentrate on getting the new HDD ready for use.

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> When I click 'format drive' I get the following options:
- Master boot record
- GUID partition table
- Don't partition
- Apple partition

Pretty sure you want Master Boot Record.

---

### Post by camel_33 on 2010-07-05
oh my, formatting the drive failed, here's the message:
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
ped_device_get() failed
Maybe things got clogged up or overheated, it's pretty hot here, I think I will just close all programs and restart, which may take some time as it's from the live-CD. I should be back in 20 min.

---

### Post by camel_33 on 2010-07-05
or wait, maybe I first try to unmount the USB flash pen drive
maybe that's interfering..

---

### Post by anandrao07 on 2010-07-05
This is really a good information. Thanks for posting.

---

### Post by camel_33 on 2010-07-05
nope, same error message
what if I first 'format volume' in DiskUtility?
or try again 'format drive' but choosing 'GUID partition table'?

---

### Post by warfacegod on 2010-07-05
You said earlier that Gparted couldn't see it. Is it listed here? See screenshot, upper right.

---

### Post by warfacegod on 2010-07-05
You said earlier that Gparted couldn't see it. Is it listed here? See screenshot, upper right. If the new drive is there use Gparted to format it.

---

### Post by camel_33 on 2010-07-05
I'm afraid I can't see it there.. if I click on the drop-down arrow it only shows dev/sda 
see screenshot in my next post

---

### Post by camel_33 on 2010-07-05
GParted (screenshot)

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> GParted (screenshot)

Aggravate, aggravate,......
(warfacegod goes outside to have a cigarette and find a tree to pound his face into. he will now be referred to as woodpeckerfacegod)

Try GUID. Try them all until you get one that will format it.

---

### Post by camel_33 on 2010-07-05
I gotta leave soon (back round 6 pm CET) but meanwhile wish to thank you and other posters for trying to help me out here. I'm not quite sure if this is allowed by the admin guys, but if this gets solved (i.e. my data recovered from the HDD) I'd like to somehow send over a serious bottle of wine (or whatever you prefer).

Perhaps before I leave, I heard of the crazy idea to deep freeze the damaged HDD (wrapped in plastic) for a few hours or even overnight. How about that if we can't solve the external HDD visibility issue? I could do that right after I shutdown the laptop and leave the house 8-[

Cheers, C

---

### Post by camel_33 on 2010-07-05
oeps, just missed yr last post
you're certainly an optimist :)
OK, I'll try that now (GUID)

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> I gotta leave soon (back round 6 pm CET) but meanwhile wish to thank you and other posters for trying to help me out here. I'm not quite sure if this is allowed by the admin guys, but if this gets solved (i.e. my data recovered from the HDD) I'd like to somehow send over a serious bottle of wine (or whatever you prefer).

Perhaps before I leave, I heard of the crazy idea to deep freeze the damaged HDD (wrapped in plastic) for a few hours or even overnight. How about that if we can't solve the external HDD visibility issue? I could do that right after I shutdown the laptop and leave the house 8-[

Cheers, C

Actually that works nicely for me. I have been delaying a desperately needed Fresh Install on my laptop and it was getting to the point where I simply couldn't delay any longer.

I assume you're talking about doing this to the old drive. I've never used the freeze method but I have heard of it. The HDD would *need* to be put into a freezer bag with as much air squeezed out as possible to help prevent condensation from building up.

---

### Post by camel_33 on 2010-07-05
I've just formatted the drive with option 'don't partition'
that didn't show any results, but maybe I can assume it's done
so perhaps I can now move to 'format volume'? (to ext4 as I believe you suggested?)

---

### Post by warfacegod on 2010-07-05
Yes, see if it works, ext4.

---

### Post by camel_33 on 2010-07-05
error message again:

Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> error message again:

Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.

I'm going to send a PM to a friend that knows more about partition tables than I do. I think ddrescue did something to the partition table of the external. You may be better off using clonezilla.

Also, I just read up on clonezilla and it turns out that the HDD to be copied must unmounted for it to work. I assume ddrescue is the same deal. So in that respect, I was wrong. However, a drag n' drop operation requires the drive to be mounted.

---

### Post by camel_33 on 2010-07-05
OK, so I'll shut down for the moment and re-boot later.
I'll let you know when I'm online again. Thanks again for all the help.
Perhaps it's worth trying to first connect the USB to IDE (external HDD) before I reboot.

---

### Post by camel_33 on 2010-07-05
hi, I'm still here.. and something happened!  
the external drive became visible on GParted after I disconnected the USB to ATA and then connected again..

---

### Post by CharlesA on 2010-07-05
See if you can create a new partition on it from gparted.

---

### Post by camel_33 on 2010-07-05
here is the screenshot
I'm a bit confused about the volume though: 2.0 TiB..

---

### Post by camel_33 on 2010-07-05
When I right-click the gray area and choose 'information' I get a warning message:
'dev/sdc unrecognized disk label'

But anyway, perhaps I'll just carry on as you suggested. 
Which new partition table to choose from, MS-DOS, AIX, Amiga, .. ?

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> When I right-click the gray area and choose 'information' I get a warning message:
'dev/sdc unrecognized disk label'

But anyway, perhaps I'll just carry on as you suggested. 
Which new partition table to choose from, MS-DOS, AIX, Amiga, .. ?

I assume it's missing reading as 2 TB because of the broken/missing partition table. How big is it actually supposed to be? Also be certain that Gparted hasn't decided that all drives in the computer a one big HDD. Aside from that, proceed.

Presumably it would have originally come with an MS-DOS part. table, so go with that.

---

### Post by camel_33 on 2010-07-05
nope, creating a new partition failed..
it resulted in the new HDD being disconnected (or at least I can't see it anymore)
I'm starting to give up here..

---

### Post by camel_33 on 2010-07-05
sorry, I hadn't yet read yr last post
but anyway, I'm getting a little desperate here

---

### Post by warfacegod on 2010-07-05
Then it's time to go do your errands and take a fresh look at this when you get back.

---

### Post by camel_33 on 2010-07-05
doesn't look good
I just disconnected the USB to ATA adapter (with new HDD)
then re-connected, but remains invisible, even in DiskUtility

---

### Post by camel_33 on 2010-07-05
OK, you're right
I'll shut down after all and see what happens if I restart (with USB to ATA drive connected)
cheers, C

---

### Post by Leppie on 2010-07-05
i have no experience with neither dd-rescue nor clonezilla.
however, testdisk is an excellent rescue program which can be installed from the repos. it has deep scan functionality (analyses the actual partition and not the partition table).

i sometimes have issue with my sd cards in lucid and apparently there's several other usb issues with the latest release. try the karmic livecd and see if it the drive mounts normally (and stays mounted until you unmount it).

---

### Post by camel_33 on 2010-07-05
Hi I'm back in business
I'm not sure how to resume this thread but I'll give it a go

I've restarted the Ubuntu 10.04 live CD with the new HDD inside, and in this way I'll try to partition this drive, so that I can create an image on this drive later on (see earlier posts why I want to do this).

---

### Post by Leppie on 2010-07-05
try installing testdisk.

did you actually already make a backup copy of the partition with the files you want to keep?

---

### Post by camel_33 on 2010-07-05
hi sorry I overlooked yr post
asaik testdisk is not really a remedy for bad sectors? but I'll have a look at it again
thanks..

---

### Post by camel_33 on 2010-07-05
Re. yr last question: no, all my files are (and have been since last week) residing on that damaged HDD and were not backed up. I know that sounds ridicilous but it's the naked truth.. I was anyway 'going to upgrade very soon' (some people never learn I guess). Though I have now, forever.
So anyway, I'm going to give it a shot, i.e. download 'testdisk' from the repositories.

---

### Post by camel_33 on 2010-07-05
I just read the description from the repos, which say:

TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32
 * NTFS ( Windows NT/2K/XP )
 * Linux Ext2 and Ext3
etc etc

but nothing about 'bad sectors', I'm not so sure if this is going to solve my problem..

---

### Post by Leppie on 2010-07-05
can you actually see the partitions on the drive now that it's in your box rather than connected via usb?
if you can see it, try to make a backup copy of the partition using dd
```
sudo dd if=/dev/sda1 | gzip /somewhere/on/new/drive/backup.gz
```

---

### Post by Leppie on 2010-07-05
> **camel_33 said:**
> I just read the description from the repos, which say:

TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32
 * NTFS ( Windows NT/2K/XP )
 * Linux Ext2 and Ext3
etc etc

but nothing about 'bad sectors', I'm not so sure if this is going to solve my problem..
well, the sectors it can't read will be skipped. but at least the data that is not affected can be recovered.

---

### Post by camel_33 on 2010-07-05
The HDD inside my laptop (or in the box as you call it :) is the new HDD, to where I want to copy the damaged HDD later.
The reason I put it inside is to partition (or prepare it) for later. If that's done, I want to take it out and replace it with the damaged HDD. Then I connect the partitioned HDD via USB, to hopefully start the cloning process (if the saints will give their blessing)

---

### Post by camel_33 on 2010-07-05
hi Leppie, I'm getting pretty desperate out here.
I'll try yr suggestion (Testdisk) but I'll first have to shutdown the laptop, in order to remove the new HDD and replace with the damaged one. Then I can connect the new HDD via USB and hopefully work with Testdisk. BBS, C

---

### Post by warfacegod on 2010-07-05
> **camel_33 said:**
> Hi I'm back in business
I'm not sure how to resume this thread but I'll give it a go

I've restarted the Ubuntu 10.04 live CD with the new HDD inside, and in this way I'll try to partition this drive, so that I can create an image on this drive later on (see earlier posts why I want to do this).

I was going to suggest doing just that. Glad you beat me to it.

---

### Post by Leppie on 2010-07-05
> **warfacegod said:**
> I was going to suggest doing just that. Glad you beat me to it.
see, must be age... :P

---

### Post by warfacegod on 2010-07-05
> **Leppie said:**
> see, must be age... :P

.................................................................................................................................................................................................................................................... more eons pass.

No, I wasn't around because I went insane and decided to install Lucid into my main partition.

---

### Post by camel_33 on 2010-07-05
how does this screenshot look to you?
with the new HDD in the box, I was able to at least format the drive.
However, when I try to create a partition (i.e. to ext4) I get an error message.
Never mind, this should be a better starting point before shutting down and swapping the drives.

---

### Post by camel_33 on 2010-07-05
ah maybe it can't be completely partitioned as a little part is used by the live CD? (just guessing)
anyway, I'm gonna shut down now and restart in 20 or so min. (and pour myself a good drink in the meantime)

---

### Post by Leppie on 2010-07-05
> **camel_33 said:**
> how does this screenshot look to you?
with the new HDD in the box, I was able to at least format the drive.
However, when I try to create a partition (i.e. to ext4) I get an error message.
Never mind, this should be a better starting point before shutting down and swapping the drives.
sorry, what is the exact error message?

---

### Post by Leppie on 2010-07-05
> **camel_33 said:**
> ah maybe it can't be completely partitioned as a little part is used by the live CD? (just guessing)
the livecd would only be able to use an already existing swap partition on a hd...

---

### Post by camel_33 on 2010-07-05
sorry, I was already gone.. i.e. I shutdown and switched the drives
now the damaged HDD (with bad sectors) is in the box, in a moment I'll connect the new HDD via the USB to ATA adapter.
that means the moment of truth is about to come (see if I can finally copy/transfer (clone) SDA to SDB.

---

### Post by camel_33 on 2010-07-05
unbelievable, again I cannot format or create a partition on the new HDD
it looks I'm not going to rescue this old HDD, unless someone has the magic to tell me

---

### Post by Leppie on 2010-07-05
why don't you try connecting your old drive using the usb cables?
you will only want read access to that drive anyways... ;)

---

### Post by camel_33 on 2010-07-05
this is the new HDD (as seen in DiskUtility)
in my next post I'll submit the error messages when I attempt to:
- format:drive (Master Boot Record)
- format volume (to ext4)

---

### Post by camel_33 on 2010-07-05
sorry, forgot the attachment

---

### Post by Leppie on 2010-07-05
again, i don't see any error message...
try using gparted?

and see [post #76]("http://ubuntuforums.org/showpost.php?p=9551877&postcount=76")__[]("http://ubuntuforums.org/showpost.php?p=9551877&postcount=76")

---

### Post by camel_33 on 2010-07-05
error messages when I attempt to

- format:drive (Master Boot Record):
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0  ped_device_get() failed

- format volume (to ext4):
Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.
 
perhaps I should try format to another ext? or NTFS? 

Anybody out there?, cause if tonight I won't succeed, I have to let it go and start rebuilding my data from scratch. I've been trying to rescue this HDD for over a week now and getting close to becoming insane.

---

### Post by camel_33 on 2010-07-05
GParted doesn't show up anything, except what's inside the box

---

### Post by camel_33 on 2010-07-05
the old HDD has bad sectors and is unreadable and unmountable
that's why the only solution (unfortunately) is to clone to a new HDD and start the rescue operation from there

> **Leppie said:**
> why don't you try connecting your old drive using the usb cables?
you will only want read access to that drive anyways... ;)

---

### Post by Leppie on 2010-07-05
> **camel_33 said:**
> the old HDD has bad sectors and is unreadable and unmountable
that's why the only solution (unfortunately) is to clone to a new HDD and start the rescue operation from there
that's what i was saying, you don't really want to mount it and only need access to read the partition at low level.

---

### Post by silversufer86 on 2010-07-14
> **camel_33 said:**
> error messages when I attempt to

- format:drive (Master Boot Record):
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0  ped_device_get() failed

- format volume (to ext4):
Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.
 
perhaps I should try format to another ext? or NTFS? 

Anybody out there?, cause if tonight I won't succeed, I have to let it go and start rebuilding my data from scratch. I've been trying to rescue this HDD for over a week now and getting close to becoming insane.

I wanted to say.. I'm not sure how you're connecting the disc. If its through a usb cable so that you can format it, does it have an SATA power source as well connected to it? Thats the mistake I made.. I forgot to connect the power source and it was just running off the power from the USB. Hope this helps..

---

### Post by camel_33 on 2010-07-20
Hi, thanks for yr post and sorry for my late reply.
Asaik the USB to IDE/ATA adapter doesn't require the power cable when connected to the new HDD, which is a Samsung 2.5" (PATA). A power cable was indeed included in the box when I bought it, but as far as I understand only necessary for 3.5" IDE and SATA connections.

I believe the reason why I couldn't 'see' the HDD, was that it wasn't (properly) formatted. I have meanwhile installed Ubuntu 10.04 on that HDD, but over 100 GB unallocated space left (see screenshot). I still hope to clone/copy the old (damaged) HDD to this partition.

Any suggestions at this point?


> **silversufer86 said:**
> I wanted to say.. I'm not sure how you're connecting the disc. If its through a usb cable so that you can format it, does it have an SATA power source as well connected to it? Thats the mistake I made.. I forgot to connect the power source and it was just running off the power from the USB. Hope this helps..

---

### Post by camel_33 on 2010-07-20
Sorry, forgot the screenshot..

---

### Post by warfacegod on 2010-07-20
Two things.

.01 You can resize the partition by: right clicking it> select Resize> drag the arrow on the right.

.02 I used to own a WD Passport 2.5 External HDD. I had to bring it back because the USB's in my laptop weren't able to supply sufficient power to it.

---

### Post by CharlesA on 2010-07-20
> **camel_33 said:**
> 
I believe the reason why I couldn't 'see' the HDD, was that it wasn't (properly) formatted. I have meanwhile installed Ubuntu 10.04 on that HDD, but over 100 GB unallocated space left (see screenshot). I still hope to clone/copy the old (damaged) HDD to this partition.

Any suggestions at this point?

You can resize partitions, but backup any data you have on the drive before you do so.

It should have automatically used all available space when you installed Ubuntu on it tho.

Most 2.5" USB drives come with a USB cable with 2 connectors on it in a Y configuration so that the drive gets sufficient power.

---

### Post by camel_33 on 2010-07-22
Hi, thanks again for yr reply

Coming back to yr 1st point, why resize the partition of the new HDD when there is enough unallocated space (over 100 GB)? Question remains if I can leave it like that (see screenshot earlier post) or should I first partition (format) in order to clone/copy from the old damaged HDD. If so, how to proceed?

> **warfacegod said:**
> Two things.

.01 You can resize the partition by: right clicking it> select Resize> drag the arrow on the right.

.02 I used to own a WD Passport 2.5 External HDD. I had to bring it back because the USB's in my laptop weren't able to supply sufficient power to it.

---

### Post by camel_33 on 2010-07-22
Hi thanks,

With regard to yr 2nd point: I indeed installed 10.04 using all available space, but later resized i.e. to create space for the cloning operation (which I'm still hopeful to do using ddrescue). But I must probably first partition (or format) that unallocated space..

> **CharlesA said:**
> You can resize partitions, but backup any data you have on the drive before you do so.

It should have automatically used all available space when you installed Ubuntu on it tho.

Most 2.5" USB drives come with a USB cable with 2 connectors on it in a Y configuration so that the drive gets sufficient power.

---

### Post by camel_33 on 2010-07-28
I'm finally set to start the rescue operation using GNU ddrescue, as I understand this is the safest way to clone my failing HDD to a new USB drive. I'm now able to see both disks in GParted, see screenshot.

What I would need now is someone to guide me through the command syntax :) I will ofcourse use a live CD for this for purpose. The idea is to copy/clone dev/sdb1 (35,70 GiB, the partition with valuable date) to dev/sda2? (106,72 GiB unallocated, see grey area). I guess I must first partition this part of the new HDD, earlier someone recommended ext4, is that OK?

Now about the order (direction) of copying: right now the new healthy disk (on which I already installed Ubuntu 10.04) is inside my laptop, the new HDD is connected (external) via USB. Can I leave it like that, or is it better the other way round? (failing HDD inside laptop, new HDD as USB drive)?

Looking forward to your feedback!

---

### Post by warfacegod on 2010-07-28
I don't know the syntax but I think Leppie does. I'll contact him.

---

### Post by camel_33 on 2010-07-28
I'm not sure that's a good idea. from what I understand I should first copy to a healthy drive and only then start the recovery process (i.e. from the clone or image).

> **Sorensenp said:**
> try to remove bad sectors in your hard disc.

---

### Post by warfacegod on 2010-07-28
It's not a good idea until you have your backup. Give it a shot afterward though. Who knows, you may be able to resurrect it for use as a backup drive. Seems unlikely to me though.

---

### Post by camel_33 on 2010-07-29
Hi, OK thanks for all yr help so far. However it seems nobody can guide me further through the command syntax, i.e. to finally proceed the ddrescue operation. I'm however glad I resolved one big obstacle: identifying the new USB drive. The trick was to start-up with the drive connected, only then it get's recognized with fdisk -l

Maybe I'll check out the linuxforums.org, in any case I'll report back in this thread once the job is done. Cheers, C


> **warfacegod said:**
> It's not a good idea until you have your backup. Give it a shot afterward though. Who knows, you may be able to resurrect it for use as a backup drive. Seems unlikely to me though.

---

### Post by warfacegod on 2010-07-29
If you don't mind creating a user account you could try posting in the link in my signature.

---

### Post by camel_33 on 2010-07-30
Not sure if I understand, don't I already have a user-account? 
Anyway I'll look into that..

---

### Post by warfacegod on 2010-07-31
> **camel_33 said:**
> Not sure if I understand, don't I already have a user-account? 
Anyway I'll look into that..

You have one here. The forum in my sig is a separate site from this one.

---

