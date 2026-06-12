---
title: "Firewire Hard Drive Problem"
date: 2006-02-15
forum: General Help
---

### Post by anmlcrckrs on 2006-02-15
I'm trying to get my firewire external hard drive to recognize under Kubuntu but every time I turn it on it says media:/sda1 not available.  I've formatted it with partitionmagic 8.0 to ext3, but I'm not sure if there is anything else I need to do to get it to recognize.  My searching through the forums hasn't gotten me anything.  

Any suggestions?

---

### Post by treris on 2006-02-16
Have you tried adding the drive through "Disk & Filesystems" in "System Settings"??

It show up in there and then you can configure how and where it's mounted to.

---

### Post by wrtrdood on 2006-02-16
Not sure what that format leaves you with but it's quite possible that you only have a drive with a partitiion designated as a Linux volume.  You may need to use mkfs.ext3 to create the actual filesystem on the drive.

---

