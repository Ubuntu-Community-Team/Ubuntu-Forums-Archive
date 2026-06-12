---
title: "Grub stage 1.5 read error.  Wierd situation"
date: 2009-10-23
forum: General Help
---

### Post by david90 on 2009-10-23
I ran my ubuntu 8.04 as a file server 2 days straight, came back and I found that the desktop froze.  I power cycle the machine and I got the message Grub stage 1.5 read error.  I powered cycle the machine about 5 times and I got some same result each time.  I opened up the machine and disconnect the other two hard drive that I setup as RAID 1 using mdadm.  To my surprise, the ubuntu started up.

is it just a coincident that something corrected itself when I disconnect my other two hard drive?.  The other two hard drive is RAID1 and I use it for storage.  Does grub ever touch other hard drive besides the hard with the OS in it?

---

### Post by earthpigg on 2009-10-23
hi,

depending on how your motherboard and/or BIOS is configured, plugging the other hard drives in may be resulting in *the RAID array* being what grub sees as the "first" and/or "primary" hard drive.

---

### Post by david90 on 2009-10-23
> **earthpigg said:**
> hi,

depending on how your motherboard and/or BIOS is configured, plugging the other hard drives in may be resulting in *the RAID array* being what grub sees as the "first" and/or "primary" hard drive.

Can you give an example of how the bios/motherboard is configured that could cause my problem?

---

