---
title: "unable to boot with AHCI enabled"
date: 2011-02-28
forum: General Help
---

### Post by sads45 on 2011-02-28
I have been running a dual-boot, Windows 7 and Ubuntu 10.10 system with the disks set for IDE with no problems.  I have just attempted to change the disk system to AHCI and, whilst I can boot into Windows 7, I am unable to boot into Linux and get the error:
"Alert! /dev/disk/by-uuid/5d773307-a046-40fa-ba29-728611bc7eed does not exist"

I am new to Linux so am unsure where to go from here.  I have reverted to IDE for the moment and it boots Ok.

Ian

---

### Post by dcstar on 2011-03-01
> **sads45 said:**
> I have been running a dual-boot, Windows 7 and Ubuntu 10.10 system with the disks set for IDE with no problems.  I have just attempted to change the disk system to AHCI and, whilst I can boot into Windows 7, I am unable to boot into Linux and get the error:
"Alert! /dev/disk/by-uuid/5d773307-a046-40fa-ba29-728611bc7eed does not exist"

I am new to Linux so am unsure where to go from here.  I have reverted to IDE for the moment and it boots Ok.

Ian

My 10.04 system boots up with ACHI or IDE, did you also have a RAID setting on?

If you boot an install CD in AHCI mode and then check the UUIDs of the Linux partitions you may see if they are actually detected.

---

### Post by sads45 on 2011-03-01
> **dcstar said:**
> My 10.04 system boots up with ACHI or IDE, did you also have a RAID setting on?

If you boot an install CD in AHCI mode and then check the UUIDs of the Linux partitions you may see if they are actually detected.

I do not have a RAID.  I have the windows 7 on one disk and the Ubuntu Linux on a different disk.

I will try your suggestion to boot an install CD later today but how do I find the UUID of the Linux partition?

---

### Post by sads45 on 2011-03-01
> **dcstar said:**
> 
If you boot an install CD in AHCI mode and then check the UUIDs of the Linux partitions you may see if they are actually detected.

As suggested, I changed my disks to AHCI then booted into Linux from the Ubuntu install CD.  When I found the UUID of the Linux partition it was identical to that reported in the error of the OP.

I then tried to perform a normal boot into Linux and it worked.  I can only assume a temporary glitch or I have an intermittent fault.

Thanks for your assistance David

Regards
Ian

---

