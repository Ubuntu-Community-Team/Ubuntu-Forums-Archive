---
title: "Ubuntu, Squeezeboxserver and 'unseen' SD card"
date: 2011-07-16
forum: General Help
---

### Post by castalla on 2011-07-16
Briefly, my system mounts the SD card at startup. I can dir the contents.

The card has group root and owner user.

Squeezeboxserver can't see the SD card directories - it lists the mounted 
/media/disk but goes no further.

Has anyone any ideas on how to make the card directories 'seen' by user squeezeboxserver and group no group?

i can't change the /media/disk via chmod or chown - just get Operation not allowed.

Setting umask 000 in profile makes no difference.

Here's the mount info:

/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077)

---

