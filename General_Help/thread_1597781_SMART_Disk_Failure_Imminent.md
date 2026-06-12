---
title: "SMART Disk Failure Imminent"
date: 2010-10-15
forum: General Help
---

### Post by ProN8 on 2010-10-15
A friend of mine asked me to help him when his Windows 7 laptop wouldn't boot.  I found out that in the past it had said something about a failing hard disk, so I booted it into an Ubuntu 10.10 live flash drive and opened the Disk Utility.  When I looked at the SMART data it said that the assessment for reallocated sector count was failing.  I did some research and found that there isn't much hope for this drive.  We've already done some backups of important data, but is there an easy way to image the entire drive and put all of the data on a new one?  We have the important files, but niether of us wants to go through reinstalling all the software on a windows machine.  I've heard of Norton ghost, but I'm looking for opinions on free alternatives and directions on how to use them.

---

### Post by teward on 2010-10-15
Well, you could try creating a new partition on a new drive and rsyncing the data off the partition to the new drive/partition, but that can be pretty dangerous if you dont know what you're doing.

***EDIT***
Oh, if the drive is INDEED failing, or has already died, then the possibility of the rsync halting because of a drive Input/Output failure is extremely high.  But that is assuming that the drive is nearing its death.

---

### Post by ProN8 on 2010-10-15
Ok, we don't have a new drive yet so I can't do anything immediately.  I've never used rsync before, so I guess I fall in the category of 'don't know what i'm doing.'  I'm working my way through the man page now; is there anything specific I should know about how to use it?

---

### Post by srs5694 on 2010-10-15
A couple of ideas: First, you could try [CloneZilla,](http://clonezilla.org) which is a Linux tool that's supposed to be able to clone most OS installations. I've never used it, though, so I can't be sure how well it works with Windows installations. (You might have to be very careful to get the new Windows partitions to start at exactly the same sector values they do now, or Windows will probably refuse to boot.)

Second, you could try [DriveImage XML,](http://www.runtime.org/driveimage-xml.htm) which is a Windows program that's available free for private use. I've used it myself to clone an installation (and to restore one later), and it did the job fine, even moving the partition to a new location.

I don't know how either utility would cope with bad sectors if the disk's bad sector count has already exceeded the disk's limits. You might want to check both of them out and prepare to use both. That way, if one fails you'll be ready to try the other without delay. Delay is your enemy here, since every time you power down the hard disk, and every minute you use it, you increase the risk of additional data loss. Until you've got a replacement drive and are ready to attempt a clone operation, *do not* use the computer!

---

### Post by efflandt on 2010-10-15
What kind of drive is it (manufacturer)?  Western Digital has their version of Acronis free for downloan that only works to image their drives [http://www.wdc.com/](http://www.wdc.com/) and Seagate likewise has a version that only images Seagate or Maxtor drives [http://www.seagate.com/](http://www.seagate.com/)

I replaced a laptop drive in someone else's laptop and sometime later WinXP refused to boot even to safe mode.  I put it in a USB enclosure and did **chkdsk /f** on that partition from another WinXP box which restored the partition with just one apparently unimportant file lost.  WinXP was then able to boot it back in the laptop.  But WD DataLifeguard confirmed that it had bad sectors.

I tried clonezilla to image the drive, but it would not work because it does a sector by sector image and failed when it could not read the bad sectors.  But WD Acronis was able to image the drive (NOT sector by sector), and successfully wrote that image to a warranty replacement drive in USB enclosure.  It worked in the laptop.

But for some reason I cannot get the Seagate version of Acronis to work in 64-bit Win7 on my new desktop PC (which has a Seagate drive that does not have any problems).  But the PC seems to have problems trying to successfully back up Win7 to DVD, so I was trying to image the drive.

---

### Post by psusi on 2010-10-15
You want either clonezilla or ghost4linux, both of which are on the parted magic cd.

---

### Post by ProN8 on 2010-10-15
Apparently it's still under warranty.  I'm not sure if I fully understand Toshiba's polices, but it sounds like they will take care of all the data recovery.  that means that this isn't my problem at all.  

I really appreciate the replies, I can always apply your suggestions next time I find myself trying to save someone's files.

---

### Post by psusi on 2010-10-15
> **ProN8 said:**
> Apparently it's still under warranty.  I'm not sure if I fully understand Toshiba's polices, but it sounds like they will take care of all the data recovery.

Yea... no.  Data recovery ( if it is even possible ) costs more than he paid for the laptop.

---

### Post by Cammaaron on 2010-10-15
> **psusi said:**
> Yea... no.  Data recovery ( if it is even possible ) costs more than he paid for the laptop.

Wouldn't such data recovery services cost as much as a car?

---

### Post by ProN8 on 2010-10-16
> **psusi said:**
> Yea... no.  Data recovery ( if it is even possible ) costs more than he paid for the laptop.

Recovery was the wrong word.  On their website I got the impression that they will transfer what's left of his files.  They do explicitly state that they are not responsible for lost data.

---

### Post by psusi on 2010-10-16
> **ProN8 said:**
> Recovery was the wrong word.  On their website I got the impression that they will transfer what's left of his files.  They do explicitly state that they are not responsible for lost data.

You mean if he sends the drive to them, and waits a few weeks for them to try and copy off what they can to the new disk, then send it back?  That seems like a colossal waste of time.  Better to make them overnight a new drive and copy the files yourself.

---

