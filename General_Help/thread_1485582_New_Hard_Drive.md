---
title: "New Hard Drive"
date: 2010-05-17
forum: General Help
---

### Post by osarusan on 2010-05-17
I just bought a new 2 TB hard disk to replace my old 175 gig one. I currently am dual-booting Lucid Lynx and Windows 7, and rather than go through the process of reinstalling both, then reinstalling all my programs, settings, and everything, I was wondering if there's a way I can just copy the partitions on my 175 GB disk to the new one, grow them to fill up the rest of the free space on the new 2 TB disk, and then plug that HD into the primary master plug on my motherboard... will that work?

I've never done this before so if someone could tell me the best way to go about doing this I would appreciate it. Thanks!

---

### Post by dcstar on 2010-05-17
> **osarusan said:**
> I just bought a new 2 TB hard disk to replace my old 175 gig one. I currently am dual-booting Lucid Lynx and Windows 7, and rather than go through the process of reinstalling both, then reinstalling all my programs, settings, and everything, I was wondering if there's a way I can just copy the partitions on my 175 GB disk to the new one, grow them to fill up the rest of the free space on the new 2 TB disk, and then plug that HD into the primary master plug on my motherboard... will that work?

I've never done this before so if someone could tell me the best way to go about doing this I would appreciate it. Thanks!

Boot of a Live CD and use gparted to copy and paste each partition.

---

### Post by fragos on 2010-05-17
Don't know about Windows but I moved partitions between drives and had things work. Your BIOS will determine which drive the MBR is loaded from. GRUB dose reference physical drives but if you add the new copy from the old then remove the old GRUB won't need to change. FSTAB uses UUID to reference partitions so regardless of which /dev your drive is recognized as it will work without change. You may require a separate operation to get an MBR you want on the new drive.

---

### Post by lindsay7 on 2010-05-17
Check to see if the disk drive you purchased has software with it on a cd.  Sometimes it will have cloning software and this should work with your system. You would start your computer with both drives installed and with the software cd in the drive.  The cloning software will prompt you on what to do.

---

### Post by osarusan on 2010-05-17
Many thanks for the answers! You guys rock!:guitar:

---

