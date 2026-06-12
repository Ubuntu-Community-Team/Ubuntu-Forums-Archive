---
title: "blkid not recognizing filesystem?"
date: 2010-06-05
forum: General Help
---

### Post by thinking on 2010-06-05
hi,

my ubuntu server has 4 2TB disks attached
im using udev on boot to mount the disks
suddenly one partition of such a hd cant be mounted
it seems that udev isnt recognizing the filesystem
anymore, all other partitions work as expected
using blkid i get a list excluding the failed partition
the mount command either doesnt recognize the filesystem
but if i mount using -t ext3 i can use it without problems
fsck.ext3 doesnt find any errors

so my question: anyone has a clue what could be wrong or a hint
what i could try to get it up and running again?
not sure if the problems began since a power outage

thx in advance

---

### Post by thinking on 2010-06-05
bump

---

