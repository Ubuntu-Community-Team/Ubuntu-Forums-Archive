---
title: "Unable to change directory permissions on automounted USB drives?"
date: 2009-12-15
forum: General Help
---

### Post by probedb on 2009-12-15
Hi folks,

Currently running karmic (32-bit) from a clean install.

When USB drives automount in Gnome directories are give full user permissions but no group or world permissions. Oddly all files are given 777?

Anyways I can't change the directory permissions on the directories either as root or as the user they belong to?

Any ideas why not?

I've actually disabled automounting through gconf-editor (?) but they still auto mount.

It's causing an issue as squeezeboxserver runs as it's own user and can't see my music drive :(

Cheers!
Paul.

---

### Post by lmarmisa on 2009-12-15
Sorry, I do not understand very well your post, but perhaps you are unable to change permissions on automounted USB drives because they do not use a GNU/Linux type file system (ext4, etx3) but a Windows type file system (fat32, ntfs).

---

### Post by probedb on 2009-12-15
> **lmarmisa said:**
> Sorry, I do not understand very well your post, but perhaps you are unable to change permissions on automounted USB drives because they do not use a GNU/Linux type file system (ext4, etx3) but a Windows type file system (fat32, ntfs).

I guess that is a possibility as it is an NTFS formatted drive.

To be honest with you, reformatting the drive as ext3 or similar hadn't occurred to me! I will give it a go :)

Cheers,
Paul.

---

