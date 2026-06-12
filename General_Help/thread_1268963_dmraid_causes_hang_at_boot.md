---
title: "dmraid causes hang at boot"
date: 2009-09-17
forum: General Help
---

### Post by AppleBonker on 2009-09-17
I'm hoping we have some storage device experts on here.  Let me explain the situation:

On my previous computer build, I had a raid 0 array for my windows boot and an SSD for my ubuntu boot.  My ubuntu disk was roughly a 80/20 split ext3/swap.  When I built my current computer, I added another pair of SSD's to run a raid 0 array with SSD's for windows and a single SSD for ubuntu.  Unfortunately, I didn't pay much attention when I mounted them in the case, and my ubuntu disk became one of the disks in my array.  I was planning on formatting anyway (complete hardware overhaul so it needed it), so I formatted as such and installed windows.  After I got windows functioning, I went to install ubuntu.  During the install (not from the alternate disk) it obviously wouldn't pick up the array, but it did show sdb as having an ext3 partition.  I didn't think much of it, and installed ubuntu on my third SSD (which happens to be sde - sdc and sdd are a raid 1 array for storage), configured my grub and booted/updated/etc.  As soon as I install dmraid, I can no longer boot.  When booting with the recovery option, it hangs right after configuring all my USB devices.

What I think is happening is dmraid is having difficulty recognizing the windows array due to the phantom ext3 partition.  I'm hoping someone has an idea about how to correct the partion table (drives sda, sdb, sdc and sdd are all pure ntfs partitions) without losing the data that is on there.  Clearly, if I lose that data it will destroy the array and windows wont boot.  It is a relatively fresh install, so there's really nothing on there I need, I just want to save the time from having to reinstall windows.  If that is my only option, so be it.  But I figure there should be a way to correct the problem without having to go that route.  Any input would be greatly appreciated.

---

### Post by AppleBonker on 2009-09-17
Well, I just went for it and deleted the partitions in sdb using gparted and Windows still boots fine.  But this raises a new question.  I am now trying to mount both my raid 0 (sda and sdb) and my storage raid 1 (sdc and sdd).  I install dmraid and while /dev/mapper shows isw_xxx_Windows and isw_yyy_Windows1 as well as isw_yyy_Storage and isw_xxx_Storage1, I cannot active or mount the array.  dmraid is listing the devices as follows:

> 
$ sudo dmraid -r
/dev/sdd: isw, "isw_yyy", GROUP, ok # sectors, data@ 0
/dev/sdc: isw, "isw_yyy", GROUP, ok # sectors, data@ 0
/dev/sdb: isw, "isw_xxx", GROUP, ok # sectors, data@ 0
/dev/sda: isw, "isw_xxx", GROUP, ok # sectors, data@ 0Any idea why this is showing as "GROUP" and not and not listing them as mirror or stripe?

---

### Post by AppleBonker on 2009-09-17
Nevermind, I've got it.  What's strange is the output of dmraid -ay does not seem correct:

> 
$ sudo dmraid -ay
RAID set "isw_xxx_Windows" already active
RAID set "isw_yyy_Storage" already active
RAID set "isw_yyy_Storage1" already activeIt doesn't show isw_xxx_Windows1 but I am still able to mount it.  I'm not sure why that is, but hopefully if I setup them up to mount at boot I'll be ok...

---

### Post by AppleBonker on 2009-09-18
So I could mount both arrays without an issue, but installation of dmraid still caused a hang at boot.  The only way to boot normally is for me to uninstall dmraid.  I'm not sure what is broken on boot, but I can reboot as many times as I like until I install dmraid.  Then I hang right before boot (I seem to initialize all my usb drives and ethernet connection).  As far as I can tell from the logs, this is the final step before boot, so it doesn't seem like dmraid broke any of my hardware configurations.  Though, I'm still kind of new to this (only been running ubuntu for a few weeks now).  Anyone have any ideas?

---

### Post by AppleBonker on 2009-09-19
Not that I like to keep bumping my own thread, but...

It turns out one of my raid0 drives had some screwy metadata on it.  That and my partion tables seemed to be a bit off.  I had to correct those issues, which caused me to lose my windows install (obviously).  Anyway, I'm reinstalling windows now, but I don't think I'll have any more problems.

For anyone else out there in a similar position, make sure you do this before you install windows the first time.  One of my raid drives was in a previous install, so Ubuntu seemed to be getting confused with how to recognize it.  Had I fixed this in the first place, I wouldn't have wasted as much time as I did thus far.  But at least I learned a lot more about storage device management in Ubuntu...

---

