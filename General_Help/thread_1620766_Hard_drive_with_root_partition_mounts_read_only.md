---
title: "Hard drive with root partition mounts read only"
date: 2010-11-13
forum: General Help
---

### Post by gnomey on 2010-11-13
Hi everyone,

A few days ago there was a power outage while my computer was switched on, this hasn't been the first time this has happened.

When I turn on my PC, I get an error that says "Cannot find / on the hard drive" or something to that effect, and it gives me three options, skip, ignore and manual recover.

Skip just brings me to a terminal login, and startx gives me a load of errors.

Ignore gives me some error about /tmp not mounting, but it disappears after a few seconds allowing me to use the computer. I can use it perfectly for a few seconds, then if I try and open any application it'll just give me a white box. I have a feeling the drive mounts read-only because of errors=remount-ro in the fstab.


I've tried running fsck on my drive, I'm using ReiserFS as the filesystem, and it asks me to rebuild-tree. I don't know anything about that so I have not done that.

What do you guys recommend I should do? I think there are errors on my drive, but fsck wants me to rebuild-tree, which form what I read can destroy data.

---

