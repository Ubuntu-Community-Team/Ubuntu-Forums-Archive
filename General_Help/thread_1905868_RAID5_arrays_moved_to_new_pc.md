---
title: "RAID5 arrays moved to new pc"
date: 2012-01-07
forum: General Help
---

### Post by snickkers on 2012-01-07
Hi all. NOOB DISCLAIMER: This is the first time I've made use of ubuntuforums.org, so my apologies if I've posted this question to the wrong board - I couldn't find any RAIDy boards, so I've just gone for "General". Secondly, I *have* done a search for similar threads from the past, but I was flooded with irrelevant posts and couldn't find anything similar to my situation. Please feel free to (politely) point me towards any relevant threads, I have a feeling I might just suck at using the search function and using the right keywords.

Ok, now that the apologies for being a noob are out of the way... In the past I had an old PC that I'd set up with Ubuntu 10.04 (or close to that version number). On that system, I created two RAID5 arrays. One was 3x250GB (500GB array), the other was 6x1TB (5TB array). I built both arrays using the pre-installed GUI app simply called "Disk Utility" (and I see in 11.10, it's still called that). It all worked quite well, and I copied my entire library across to these arrays. But after about 6 months my power supply died. And so for a while now that pc has been sitting in the corner collecting dust.

Recently I decided to resurrect my RAID arrays. I bought a new motherboard & cpu, power supply, and connected up all the hard disks. I've booted to a ubuntu 11.10 live cd, and I thought that ubuntu would automatically detect and reconstruct my RAID arrays. Well, no such luck. Ubuntu 11.10 detects all individual hard drives, and detects they're all members of a RAID array, but it doesn't seem to detect anything more than that - I don't know if it recognises that they're RAID 5, and it seems to think all 9 drives form a single RAID array. And when I look at the RAID Array "state", it says "Not running, not enough components to start".

If anyone can help me out here, I would really appreciate it, because I'm lost. I'm not familiar with the raid terminal commands (mdadm?) but I'm not afraid of the bash prompt. I'd really like to be able to save all my data on the arrays if possible.

---

### Post by rsvancara on 2012-01-07
Did you have a separate boot drive?  I can not remember if Linux can boot off a RAID 5 array.  I know it can boot off a Mirror or RAID 1 software raid partition.  

My RAID information is stored here:

/etc/mdadm/mdadm.conf

---

### Post by snickkers on 2012-01-07
The old system used to boot from a USB drive separate from the RAID arrays. I don't know what I did with that USB drive though, I can't seem to find it among all my junk. I'll have a harder look for it though, because it sounds like that config file has the key missing information.

---

### Post by snickkers on 2012-01-07
Here are some screenshots that might help.

Also, I didnt mention it before but I should say that this was all linux software RAID, I didnt use any fakeRAID or hardware RAID. Also, my motherboard has 6 SATA connectors, and I have an extra 4-port PCI SATA controller card.

---

### Post by snickkers on 2012-01-08
I've had a thorough search through my things, and I haven't been able to locate my original usb boot drive. So I think we have to assume it's lost.

Is there anything I can still do to try to retreive my data? Is there a more appropriate board you'd recommend I post this to?

---

### Post by snickkers on 2012-01-14
Good news and bad news. GOOD: I've finally located the original boot drive that had the RAIDs configred on it. BAD: There's nothing useful in mdadm.conf:> 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 19 Jun 2011 19:24:12 +0800
# by mkconf $Id$

How safe would it be for me to simply plug this boot drive into the new computer and boot from it?
OLD SYSTEM: Ubuntu 10.04 [i386 desktop .iso install] (I'm pretty sure - is there a file on the drive I can check for that info?) on an Intel Atom / VIA mobo (one of them low power cpu-soldered-to-the-mobo systems).
NEW SYSTEM: Intel Core i3 / ASROCK mobo
I know an i386 live cd is fine to boot both of these computers, but the live cd auto-detects everything about the computer on boot up. I don't know how auto-detecty a properly installed ubuntu system is, and so how portable a ubuntu boot disk is?

---

### Post by Seq on 2012-01-15
> **snickkers said:**
> Good news and bad news. GOOD: I've finally located the original boot drive that had the RAIDs configred on it. BAD: There's nothing useful in mdadm.conf:
How safe would it be for me to simply plug this boot drive into the new computer and boot from it?
OLD SYSTEM: Ubuntu 10.04 [i386 desktop .iso install] (I'm pretty sure - is there a file on the drive I can check for that info?) on an Intel Atom / VIA mobo (one of them low power cpu-soldered-to-the-mobo systems).
NEW SYSTEM: Intel Core i3 / ASROCK mobo
I know an i386 live cd is fine to boot both of these computers, but the live cd auto-detects everything about the computer on boot up. I don't know how auto-detecty a properly installed ubuntu system is, and so how portable a ubuntu boot disk is?

You should be fine to give it a shot.

However, on the machine you pasted the Disk Utility screenshots from, could you paste the contents of /proc/mdstat?

---

### Post by snickkers on 2012-01-16
A big thanks to rsvancara and Seq for giving my situation some attention, I was feeling very much out of my depths here. I'm over the moon to be able to report that I've solved my problem on my own now.

I was able to boot to my old USB stick (which ended up being Ubuntu 11.04, so a bit more recent than I realised), and the system recognised two separate arrays with the correct disks assigned. The 3-disk array started fine, but the 6-disk array had two of its disks marked as missing/failed. Anyway, to cut the long story short, I was able to google for a solution to that problem, and I've been able to bring up 5 out of the disks of the array, which is enough to get the array running and allow me to retrieve the data off it.

Thankyou again for your support.

---

