---
title: "ext4 to ext3"
date: 2010-11-04
forum: General Help
---

### Post by monkeytaichi on 2010-11-04
So if possible I'd like to change my /home partition from ext4 to ext3. Is there anyway to do this without having to reinstall ubuntu?
The way I'm currently thinking about doing it is backing up everything on my /home partition, reformatting it, and reloading the data back on. (all done on a live cd). Would this work?

---

### Post by linux18 on 2010-11-04
I only have one thing to say...

WHY?!?

---

### Post by sikander3786 on 2010-11-04
If you've got a separate /home partition, you can do what you mentioned.

---

### Post by jocko on 2010-11-04
Yes, it can be done that way, but you also have to make the appropriate changes in /etc/fstab to make sure the new partition is mounted.
Not that I can see why anyone would want to change from ext4 to ext3...

---

### Post by Quackers on 2010-11-04
I was under the impression that greatly experienced Linux users use ext3 by choice. I've heard one or two unnerving things about ext4 myself, and was going to ask this question too :-)

---

### Post by monkeytaichi on 2010-11-04
I'm switching back because I dual boot and I'd like to have access to my files in Windows. I recently found out its possible to view ext2 & ext3 in windows. Made me very happy.

---

### Post by linux18 on 2010-11-04
I heard ext4 is backwards compatible allowing you to use that with windows even if it doesn't say it works with windows

---

### Post by jocko on 2010-11-04
> **linux18 said:**
> I heard ext4 is backwards compatible allowing you to use that with windows even if it doesn't say it works with windows
That's wrong. The ext2 driver for windows (ext2IFS) can read/write to ext2 and ext3, but it does not work at all with ext4.
The ext2IFS driver is not very stable anyway and require constant reboots and occational reinstalls to be able to access ext2/3 (at least that's my experience from using it in windows XP). And it has not been updated since 2008, so I'm not sure if it works in windows 7 (or even with the latest service packs on XP or vista)...
My advice is that you make an ntfs partition for sharing files between windows and linux. Linux handles ntfs very well nowdays...

---

