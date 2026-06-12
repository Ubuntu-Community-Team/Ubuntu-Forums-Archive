---
title: "HAL issue"
date: 2010-05-30
forum: General Help
---

### Post by NothingNow on 2010-05-30
I was trying to burn a CD today and for some reason HAL is not mounting the CD-ROM when i insert a blank or CD with things on it.

What could be causing this issue and what do i need to do to fix it.

---

### Post by DagMan on 2010-05-30
Is it a new problem on this machine or were you previously able to mount disks?
Are you able to mount things manually if you do** sudo mount /dev/cdrom** ?
Can you post the contents of your fstab by opening a terminal and typing **cat /etc/fstab** please.
Is there a mount point for the cdrom in the /media folder?  It would be a folder that said cdrom or cdrom0

---

### Post by NothingNow on 2010-05-30
ive honestly decided that i dont want ubuntu anymore on my computer i will be going back to something like arch or gentoo were i can do what i want and as i please with my system...

---

### Post by DagMan on 2010-05-30
Fair choices.
I'm guessing you're already aware, and further I don't know if this is still a problem with the kernel drivers, but one thing to check, which will be important for either of those distros as well, is the whole compatability mode and enhanced mode in the bios that was seen back when there was the change from XP to vista.  I had problem a few years back when I tried to use the optical drive because it needed to be in compatible mode.  I would imagine that would have been integrated into the kernel by now but thought it was was still worth mentioning.  It was a matter of the optical drive being seen as ide vs sata or something along those lines -hardware specifics isn't my thing.  I suspect you know what I'm on about though - it would suck to get partway through compiling a desktop in gentoo only to have your optical drive refuse to idle back up, or to get all the way through and find you still have the same problem.

---

### Post by dcstar on 2010-05-31
> **NothingNow said:**
> I was trying to burn a CD today and for some reason HAL is not mounting the CD-ROM when i insert a blank or CD with things on it.

What could be causing this issue and what do i need to do to fix it.

10.04 no longer uses HAL, so it is no wonder it isn't mounting anything.

---

### Post by NothingNow on 2010-06-01
> **dcstar said:**
> 10.04 no longer uses HAL, so it is no wonder it isn't mounting anything.

Well in this case you should not be able to install apps that require HAL... and as far as compatiblity goes i have used arch for about 2 years now and just thought i would try out Ubuntu and honestly was not impressed what so ever...

---

### Post by dino99 on 2010-06-01
maybe too easy for a Gentoo techie guy, but mountmanager is a friendly boy to deal with partitions and devices, install it and set your prefs as you need into: system admin mountmanager

---

