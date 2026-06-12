---
title: "Device id changes on power on vs warm reboot"
date: 2011-11-26
forum: General Help
---

### Post by SirWeazel on 2011-11-26
When starting ubuntu 11.10 from completely off vs soft/warm restart causes the drive to change.

From cold start:
Sata port 1 (os drive) = /dev/sda
Sata port 2 (data drive) = /dev/sdb
Pata port 1 (ide cable, old vista drive now is just data) = /dev/sdc

After a restart (NOT POWERED DOWN):
Sata port 1 (os drive) = /dev/sdb
Sata port 2 (data drive) = /dev/sdc
Pata port 1 (ide cable, old vista drive now is just data) = /dev/sda

This causes a problem when i try to make mount points, other than that it doesn't appear to cause a problem. I'm not even sure how ubuntu boots correctly when it is giving wrong id's/locations.

How can i fix this, or how can i make mount points easily by using something else that doesn't change, ie. serial#'s maybe??

Info/specs:
Ubuntu 11.10 64bit (not sure if this occurred with other releases or not), Asus A8N32-SLI Deluxe motherboard with AMD Athlon 64 FX-60.

Let me know anything else you might need, and how to obtain it. Thanks in advance for any help!

---

### Post by fragos on 2011-11-26
One solution is to mount the drives in fstab with their UUID which doesn't change. I've seen a similar situation with video devices like webcams and TV cards which are both assigned /dev/video[0/1]. In that case I created udev rules to add different mount points which I then placed in configurations of applications like TVtime.

---

### Post by SirWeazel on 2011-11-28
Cool thanks, I've always been slightly confused by mounting drives. Your tip gave me something new to search for. I was missing the UUID part to my problem.  I really wish this task would be much easier (GUI) in ubuntu. But it looks like the ubuntu documentation has been updated, or i understand it more this go-around/reread then i did a couple years ago.

According to the documentation, Ubuntu now recommends to use UUID instead, see the instructions here:[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID).  This sounds like the way to go.

Ubuntu documentation links:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I'll post back with my findings, tips, and overall expierence when i get it working. But i still think this function should be built into "Disk Utility" in the future. I tried some of the other gui utilities out there, but they are outdated and don't use the UUID.

Any tips before i dive into the fstab, please let me know?

---

### Post by fragos on 2011-11-28
I doubt I can add much to your research. Although not an answer to specific and appropriate request In 11.10 I installed "Disk Utility" which I find very helpful. It was around in the 9.10 time frame but I don't recall what it was called for Synaptic to install. For disk partitioning you can't beat gparted.

---

