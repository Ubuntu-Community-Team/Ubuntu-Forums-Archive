---
title: "Ubuntu Server can't detect scsi hdd"
date: 2010-04-26
forum: General Help
---

### Post by smay84 on 2010-04-26
Hi

I'm running Ubuntu Server 9.10 as a VM in Hyper-V.

I wanted to attach a vhd to it but realised a reguler IDE drive had a size limitation.  I switched the drive over as a scsi and now Ubuntu can't detect it.  Any ideas why?

Si

---

### Post by smay84 on 2010-04-26
Just tried installing scsitools and rthen running rescan-scsi-bus.sh to detect any new drives.  It doesn't find anything.

If i run fdisk -l it only shows the initial drive i used to install ubuntu and now the new one.

---

