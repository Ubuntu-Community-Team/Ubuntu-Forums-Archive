---
title: "Need advice"
date: 2009-10-12
forum: General Help
---

### Post by Mikechap on 2009-10-12
HI,

I am running a duel boot system running windows 7 (RC)/Ubuntu 9.10 (Beta) on my Acer Aspire 3003 Lci laptop. I just replaced the DVD drive with a Samsung SN-S082 drive. My problem is when I play a DVD in the VLC media player, I can't get the drive to open afterward. When I use the emergency release the drive keeps spinning the disk,  you can see the laser moving, and the DVD icon on the desktop won't go away. _**This does not happen when I am in windows.**_ I think this is a bug in Ubuntu, but can't figure out how to report it. I am at a loss, and I will be removing the beta off my laptop tonight and going back to 9.4, as this could be a dangerous bug, because if the drive is open with a disk in it and starts spinning it could cause serious harm.

---

### Post by Giblet5 on 2009-10-12
It could cause harm to a small beetle or fly. Maybe. If the fly or beetle jumped into the tray just as it started to open, it could skin a knee, I guess.

The ability to open the drive while it's spinning is managed by the drive, not Ubuntu.

Now, why the drive keeps spinning is something you'll have to look at in terms of "what is reading from the CD" and "how do you get it to cut that out".

Some CD drives can be opened while the CD is being read, but they'll disable the laser(s) and spin the disk down before opening. These drives signal a read error due to an opened tray. Any program reading the DVD can 'see' that the tray was opened and handle the read error correctly.

My HP dvd1070 drives do that. I call this a "Good Drive".

My Pioneer DVD writer in the system next to this does NOT do that. That drive can't be opened if something is reading the drive. In Ubuntu, I have to unmount the CD or the stupid drive won't open because the eject button doesn't signal the driver to unlock and eject. I call this one a "Bad Drive that will get tossed as soon as I get around to replacing it."

Windows doesn't behave that way. Does that make it an Ubuntu bug? No, it's just different behavior; Windows doesn't lock the drive and it's a retarded optical drive.

---

### Post by Mikechap on 2009-10-12
I will know for sure soon. I am reinstalling Ubuntu 9.04. I plan to test this issue afterward. I will report back here what I find.

---

### Post by Mikechap on 2009-10-12
I just finished several hours of updating. I removed windows 7 and Ubuntu 9 10 beta off my laptop. Its now running Vista and Ubuntu 9. 4. After several minutes of testing, the DVD player is NOT doing what it was. There is NOTHING wrong with any of my hardware, yes I suspect there is a bug in the ubuntu 9 10 beta.

---

