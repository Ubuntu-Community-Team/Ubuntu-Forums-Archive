---
title: "Drives listed under /media + Kubuntu early impressions"
date: 2006-03-20
forum: General Help
---

### Post by dartmusic on 2006-03-20
First, let me say that I'm definitely still a noob, but learning quite a bit fairly quickly.  My Linux experience started last December with SuSE 10, but after much frustration, I finally decided to try Kubuntu about two weeks ago.  Yep, I jumped in head first and smacked myself in the face on the bottom of the pool.  I quickly uninstalled and re-installed SuSE only to run headlong into the things I really didn't like about it.  After taking a deep breath and slowing down a bit, I reinstalled Kubuntu (Breezy, by the way) and haven't yet looked back.  All-in-all I'm much happier and seem to be able to not only find solutions to problems I encounter (likely because of the friendlier and larger user base), but many more interesting "tips and tricks" and HOWTOs.  So, in a way I want to say "thanks" to the community at large for making the transition (as well as the Windows detox) relatively painless.

So, now comes my question:  I've been playing around with mounting options (I'm using an HP notebook with 3 USB HDs - 2 ext3 filesystems and one still on vfat that I don't want to convert), and in the process I've ended up with a BUNCH of different "drives" listed under /media.  Of course, only those currently mounted do anything, but I really want to delete all those that are not actually pointing to anything.  Anal-retentive...me?  I'm not at home right now, so I can't post my fstab, but suffice to say that it currently only lists the appropriate entries/drives: the XP partition (yeah, I know, but I still need it for music writing/recording), the swap, the Kubuntu installation partition, and my three external drives.

Any ideas?

Thanks!

---

### Post by ltmon on 2006-03-20
You can pretty much safely delete anything from /media that isn't listed in fstab.  HAL (hardware abstraction layer) will just recreate the mount point automagically next time you plug the device in.

Cheers,

L.

---

### Post by dartmusic on 2006-03-21
Thanks for the reply.  I tried going to /media in Konqueror and deleting the folders for mount points that are no longer valid, but I get an error every time saying that they cannot be deleted.  

This isn't crucial, but it IS kind of a pain to have to scroll through a list of useless mount points to find the one that I want.

---

### Post by randcoop on 2006-03-21
You don't have permission as user to delete the files.  Start konqueror as root (sudo konqueror) and then navigate to the media folder.  You'll be able to delete the files.

---

### Post by dartmusic on 2006-03-21
Duh...I should have thought of that!!

Thanks.

---

