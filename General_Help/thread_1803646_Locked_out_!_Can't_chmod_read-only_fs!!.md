---
title: "Locked out ! Can't chmod read-only fs!!"
date: 2011-07-13
forum: General Help
---

### Post by Dscottmc7 on 2011-07-13
I guess I need some serious help, here.  THANKS.
-Been trying all sorts of methods to mount 2 CDROMs at the same time.  "Disk Utility" sees them both but will mount only cdrom (Block sr1) and not cdrom1 (Block sr0) [even if disc inserted into cdrom1]. Gave up on every option for fstab.
-Reading for days and finally read about the same problem.  He said, "Just put a blank cd in each drive, restart and it'll come up fine."  I did.
-The reboot crashed in the cmd line w/ networking (DCHI).  That crash caused virtually ALL my crucial ubuntu sys files to be "read-only," including GRUB2.
[I think Installing dpkg screwed up the whole system]
--Boot recovery to the cmd, & sudo chmod 755 -R "filename" didn't work ("READ-ONLY FILE SYSTEM")
--went to Live CD.
----mounted sda HD.  
----Found UUID of HD ...cd /xxxxxxx"uuid of HD"
----sudo chmod 755 -R /var/lib/dpkg...
----That worked!  Reboot...same crap!! (not saved...no option)
----Live CD, routine above again but took out Live CD just before restart
--Same result.  Tried everything I can...anybody know what I can do?

-->Thanks much.
[The crashed is HP m7674n -64 Pavilion, Intel DuoCore, 2 - 200Gb.Int.HDDs, 4Gb.basic RAM, Nvidia 7300le card, running Ubuntu 10.04 -64.  I have a second HP-Pavilion Elite 110f-AMD Phenom IIx4 925 -64, 8Gb.doubleRAM, 1Tb.and 2Tb.internal HDDs, ATI Radeon HD4350.  That's what I'm on right now...but I don't dare try anything else to mount both CDROMs in this one...till I can fix the other]
--In a world of hope!!
Scott

---

### Post by howefield on 2011-07-14
Thread moved to *General Help*.

---

### Post by matt_symes on 2011-07-14
Hi

Have you run fsck on your hard drive from the live CD ?

Kind regards

---

