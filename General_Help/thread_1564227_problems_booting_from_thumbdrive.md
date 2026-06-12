---
title: "problems booting from thumbdrive"
date: 2010-08-30
forum: General Help
---

### Post by dwsdad on 2010-08-30
I have 10.4 loaded on a 4Gb thumbdrive and it's been working great up until this morning.  This is an install on the thumbdrive, not a "LIVE" boot.

This morning after the Ubuntu splash screen, I get:
(process:363): GLib-WARNING **: getpuuid_r():failed due to unknown user id (0)

I've seen a post about getpwuid_r, but haven't seen one related to what I see.  Is there a way to fix this, or do I just need to re-install?  BTW, I've tried fsck, but it came back with :

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Is a directory while trying to open /media/PENDRIVE

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

