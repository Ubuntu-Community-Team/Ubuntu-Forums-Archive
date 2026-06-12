---
title: "Need some help, something to do with Sectors"
date: 2010-11-09
forum: General Help
---

### Post by Ignoble on 2010-11-09
My laptop has been wrecked for a while (probably from a virus) so I decided to totally erase the hard drive and then put Ubuntu on it. 
I love Ubuntu, and it actually loaded properly onto my laptop (More than Windows 7 could do), but when I turned my computer off and back on again, it couldn't load due to some weird errors.

Anyway, I put Ubuntu on again and haven't turned of my laptop yet. I went to look through the SMART Data things and I found red text in

Reallocated Sector Count
Normalized: 100
Worst: 100
Threshold: 50
Value: 154 sectors

AND

Current Pending Sector Count
Normalized: 100
Worst: 100
Threshold: 0
Value: 2 sectors


What does this mean, and can it be repaired easily, or is my hard drive totally trashed for good? I don't know if this matters, but it's an old (4ish years) Toshiba laptop that originally Windows Vista on it. Please explain everything as best you can!

---

### Post by sohlinux on 2010-11-09
sounds like you have some bad sectors, you can try to run fsck but the disk must be unmounted so you need to boot from the Ubuntu Live CD and then open a terminal and type.. sudo fsck -pcfv /dev/sda

sda is your disk, maybe its sda1, but you can check that in the disk utility program under admin disk utility fsck-pcfv should mark all the bad sectors as bad so the sectors are not written to.

---

