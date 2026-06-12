---
title: "HELP! Missing partitions, and I can't boot!"
date: 2009-06-29
forum: General Help
---

### Post by JayRott on 2009-06-29
Ok, I think I have a new one. I left my house this morning any everything was fine. When I came home I tried to play some mp3's and the 2nd partition on my hard drive where I keep all my backups and files I don't want to loose won't open. It said something to the affect of "can't mount the media in the drive" I restarted my computer and then I got a "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" I tried to fix grub and that gave me my boot loader back, but when I clicked on my Ubuntu installation it said that it did not exist. I can see my ubuntu partition from the live cd, but not my backup partition, ans when I look at it with Gparted it shows that the hard drive is only 30gigs (it's 60)...... I'm scratching my head. Any idea's

---

### Post by TeoBigusGeekus on 2009-06-30
Only thing I can think of is to boot up with the live cd and attempt fsck on your partiotions (provided they're not ntfs - fsck doesn't work on ntfs).

---

### Post by JayRott on 2009-06-30
ok i'm not sure what that is, but my backup partition is NTFS. any suggestions?

---

