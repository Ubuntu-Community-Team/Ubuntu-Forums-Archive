---
title: "Can't boot -- hardware or software problem?"
date: 2009-08-20
forum: General Help
---

### Post by dr_pressure on 2009-08-20
Hi,

I'm running Ubuntu with encrypted LVM, and I've had two issues with it failing to boot.

It loads grub fine, but before it asks me to enter my password it just reboots itself.

The first time this happened it was stuck in a continual reboot loop until I powered it off, and then it was fine.

I reinstalled Ubuntu and it was fine for a while, but recently it happened again -- this time it only rebooted itself once and then it was fine.


Could this be an issue of a failing SSD? Is there a way I could test it and find out?

Thanks!

---

### Post by dearingj on 2009-08-20
I've had this problem on one of my computers before. Turned out the cable which connected the hard drive and motherboard had come slightly loose.

---

### Post by dr_pressure on 2009-08-20
It's a PCI-e SSD which is screwed in, so don't think it could come loose.

Anybody know how I can check if the SSD is failing

---

### Post by tgeer43 on 2009-08-20
> **dr_pressure said:**
> It's a PCI-e SSD which is screwed in, so don't think it could come loose.

Anybody know how I can check if the SSD is failingI've never had a Solid State drive but you could check the manufacturer's website to see if there's any diagnostic software for it or if it has SMART (Self Monitoring And Reporting Technology.

Also, try running fsck on it. Use 'man fsck' in a terminal or in Google for details on the fsck command. Use with caution - it's a powerful and potentially dangerous command. Above all else, make sure the drive is _**not mounted**_ before running fsck on it.

tgeer

---

### Post by Gen2ly on 2009-08-20
A normal fsck should do fine and fsck will spit out a big fat warning if you try to check it while mounted so it's all pretty straight forward.  Here's the advice I saw once of checking for bad blocks:

> > Are there any tools (Linux programs run from Live CD's) available that
> will check for & -repair- (or re-allocate automatically) bad sectors ?

Not exactly. However, you can use the "-c" option in e2fsck for
ext2/3. This will invoke "badblocks" automatically and use the info to
mark the blocks that are bad.

Never had to go this far myself though, so it's untested.

---

### Post by dr_pressure on 2009-08-20
Thanks guys I'm going to try running fsck from within a livecd

---

### Post by dr_pressure on 2009-08-20
Fsck can't recognize the partition because I've got encrypted lvm set up. Any suggestions, or am I looking at a re-install?

---

### Post by tgeer43 on 2009-08-20
Sorry guy, I don't have any experience with encrypted lvm.
Hopefully someone else on here can help you.

tgeer

---

