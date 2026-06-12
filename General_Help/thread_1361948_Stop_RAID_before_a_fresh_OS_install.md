---
title: "Stop RAID before a fresh OS install?"
date: 2009-12-22
forum: General Help
---

### Post by Th3Professor on 2009-12-22
I'm using mdadm for raid5, my operating system is on a hard drive *separate* from the raid set-up. Do I need to "stop" my raid before I put a fresh system on the computer?

Thanks!

edit-
I also have LVM running alongside the RAID5. Do I need to do anything with LVM before I put ubu 9.10 on?

---

### Post by QrK0 on 2009-12-23
The problem installing a new operating system could be at time of identify the "correct" disk where to install.
If you are not sure, and you can "unplug" the raid system because is an external device, then do it.

---

### Post by QrK0 on 2009-12-23
The problem installing a new operating system could be at time of identify the "correct" disk where to install.
If you are not sure, and you can "unplug" the raid system because is an external device, then do it.

---

### Post by Th3Professor on 2009-12-24
I'm not sure I understand what you're saying. I don't have a raid card (hardware). I'm not using the motherboard-based fake raid. I'm using soft raid via mdadm. I wasn't sure if I have to issue a "--stop" command option or similar w/ mdadm prior to installing the new OS. Though, I don't think I do. (???) I think I just leave it alone and after I install a new OS if there is no recognition of the raid/lvm disks that *maybe* all I do is install mdadm & lvm2 on the new OS and run mdadm's "--assemble" for the raid5 and a "vgchange -a y" command for the lvm. I don't know. (???)

---

### Post by Th3Professor on 2009-12-26
Ubuntu Studio 9.10 installed fine, and even the raid/lvm set-up is working fine. :D There was no need to stop raid or anything. It was all automatic, part of the install process (alternate disc), including the raid5 and the lvm set-ups.

---

### Post by QrK0 on 2009-12-28
Sounds good!

Is this post related to you other [post]("http://ubuntuforums.org/showthread.php?p=8569659#post8569659")?

And if it is solved, please change the title adding [SOLVED] 

Regards!

---

