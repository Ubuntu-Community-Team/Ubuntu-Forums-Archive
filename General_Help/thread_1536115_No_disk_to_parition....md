---
title: "No disk to parition..."
date: 2010-07-21
forum: General Help
---

### Post by NaTeY` on 2010-07-21
Okay, so I was given this PC, I don't know the specs but when I try to load Ubuntu it can't find a disk to parition, I tried installing XP Pro and says it can't find any disks to install it on, how can I fix this?

---

### Post by staf0048 on 2010-07-21
Sounds like the person who gave it to you removed the hard drive or it's simply broken.  Either way you'll have to buy a new hard drive.

---

### Post by prodigy_ on 2010-07-21
Have you checked the BIOS? Does any HDD show up there?

---

### Post by NaTeY` on 2010-07-21
I've heard something about slaving, haven't looked into it...

---

### Post by WorMzy on 2010-07-21
Is there a disk in it?

Try booting a LiveCD with the nodmraid flag (When it starts booting the LiveCD, press F12 (I think) and select the option there), if that shows a hard disk after that, then you have RAID enabled in the BIOS, and, presumably, the RAID is broken, which is stopping the disk showing up normally. If this is the case, then you'll need to disable RAID in the BIOS, then the disk will show up normally in any OS.

---

### Post by NaTeY` on 2010-07-21
> **WorMzy said:**
> Is there a disk in it?
 
Try booting a LiveCD with the nodmraid flag (When it starts booting the LiveCD, press F12 (I think) and select the option there), if that shows a hard disk after that, then you have RAID enabled in the BIOS, and, presumably, the RAID is broken, which is stopping the disk showing up normally. If this is the case, then you'll need to disable RAID in the BIOS, then the disk will show up normally in any OS.
 I ordered the Ubuntu 10.04 LTS CD and I'm currently using that, I load it, says strike the f1 key, then brings me to the installation, how would I disable the RAID?

---

### Post by WorMzy on 2010-07-22
You should be presented with a menu almost immediately after the screen initially turns purple, if you don't see it, try pressing the up and down keys repeatedly to try and bring it up.

This is what the menu used to look like, it should still look similar to this:
[IMG]http://img697.imageshack.us/img697/1385/vistaubuntu05articlewid.jpg[/IMG]

Yo need to press F6 to get the nodmraid option.

---

