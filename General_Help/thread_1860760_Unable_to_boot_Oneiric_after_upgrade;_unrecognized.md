---
title: "Unable to boot Oneiric after upgrade; unrecognized filesystem"
date: 2011-10-15
forum: General Help
---

### Post by aEx155 on 2011-10-15
Not sure if the two are related, but right after I upgraded (a few days ago) I was having a lot of problems with Oneiric. Multiple restarts, programs would not load. Ended up not being able to boot Oneiric for some reason. I am not sure what caused it.

Using a LiveCD of 11.04 I tried mounting the partition but it does not recognize the filesystem type. Checking the partition with Disk Utility is finds errors but provides no solution. I am able to mount the NTFS partition on the same drive (dual boot).

As of this post I have gotten another hard drive to install 11.04 onto, but I would still like to at least be able to mount the partition to retrieve a few files.

---

### Post by DrDaveyAtoms on 2011-10-15
I am experiencing a similar problem (I have just posted on the same forum) and although I will not be able to resolve your problem I would like to ask can you not boot into recovery mode? I can and I am able to see my home drive and the rest of my files. Perhaps, you could dump them on an external disk before reinstalling?

Sorry I can't be of more help.

---

### Post by Calerid on 2011-10-15
One thing I have experienced is that if the AHCI option is set in BIOS and not Compatible it may cause this. It sometimes switches if the BIOS resets. Try finding and changing it if you can.

---

