---
title: "Need help automounting storage drives, does not work anymore"
date: 2010-05-21
forum: General Help
---

### Post by flatland2d on 2010-05-21
I have a home server with two internal hard drives for storage.  I was running 9.04 for a while, but decided to upgrade to 10.04 since it was a LTS.  I was pretty disappointed with the problems I encountered with it so I switched back (complete reinstall of 9.04 on new drive).  But now, my drives are not auto mounting and I can't mount them once booted up, either.

This is a piece of my fstab:
UUID=e70c15a4-23f7-466b-a37f-1bcdbb5d261e	/media/backup	ext3	defaults,relatime	0	0
UUID=4ad53e16-307e-4668-91c0-79b272ab1f66	/media/primary	ext3	defaults,relatime	0	0

The drives primary and backup show up under the Places menu, but if I click on them, it says I don't have privileges to do so.

Sudo fdisk -l shows the drives are there, but sudo mount /dev/sdb1 (my primary) does not mount because it says /media/primary does not exist.

I'm pretty worn out from trying to get my server up and running again so any help would be greatly appreciated.  Thanks.

---

### Post by dcstar on 2010-05-22
> **flatland2d said:**
> I have a home server with two internal hard drives for storage.  I was running 9.04 for a while, but decided to upgrade to 10.04 since it was a LTS.  I was pretty disappointed with the problems I encountered with it so I switched back (complete reinstall of 9.04 on new drive).  But now, my drives are not auto mounting and I can't mount them once booted up, either.

This is a piece of my fstab:
UUID=e70c15a4-23f7-466b-a37f-1bcdbb5d261e	/media/backup	ext3	defaults,relatime	0	0
UUID=4ad53e16-307e-4668-91c0-79b272ab1f66	/media/primary	ext3	defaults,relatime	0	0

The drives primary and backup show up under the Places menu, but if I click on them, it says I don't have privileges to do so.

Sudo fdisk -l shows the drives are there, but sudo mount /dev/sdb1 (my primary) does not mount because it says /media/primary does not exist.

I'm pretty worn out from trying to get my server up and running again so any help would be greatly appreciated.  Thanks.

/media is a **system folder** that is meant for removable devices, users should not touch that folder. Create mount points somewhere else.

---

### Post by ryan858 on 2010-05-22
> **dcstar said:**
> /media is a **system folder** that is meant for removable devices, users should not touch that folder. Create mount points somewhere else.
Um... but then he wouldn't see them in Places or Computer, correct? I don't know what's wrong with just creating a couple directories in /media... I've done it, no ill effects.

You can just ```
mkdir /media/backup /media/primary
```The /media in Ubuntu acts differently than most distros' media folders... It doesn't contain presets and stuff, it comes blank by default and Ubuntu creates directories named after the "display name" of the device, when it mounts something automatically.

But if someone has something definitive that disproves this, then please correct me.

---

