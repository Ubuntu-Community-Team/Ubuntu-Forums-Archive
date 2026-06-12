---
title: "Karmic Netbook Release stops auto-mounting drives"
date: 2010-02-27
forum: General Help
---

### Post by Laibcoms on 2010-02-27
Hi,

I installed UNR recently and after a few days, it stopped auto-mounting anything not part of its default installation.  Meaning, it won't auto-mount anything plugged via the USB **as well as** any other drives or partitions I added to fstab.

Everything seems to be correct especially since it works fine on my desktop and I have exactly the same configuration (of course except for the UUIDs).  I have to manually go to Disk Utility just to mount and eject/unmount.

UNR also stopped showing 'detected' and 'mounted' drives via the "Files and Folders > Volumes" section, even tho the system detects these drives/partitions (eg. via Disk Utility or blkid).

I have the permissions for the logged-in user set.
I have the nautilus automount setting checked (it was never unchecked).
For the fstab part, the UUIDs are correct and everything else.
For the USB part, well, just like the fstab part, no auto-mounting at all.

I'm out of clues ^^  I hope someone can help.

Thanks!!

---

### Post by scobes on 2011-02-24
I'm having the same problem with 10.04 netbook edition, can't find any explanation of it anywhere.  I have one NTFS partition which used to show up in Volumes, now there nothing there, and nothing happens when I plug in a USB drive.  fdisk and dmesg report that it knows the drive's there, and it's setting up a /dev/sdX entry for it, but nothing happens.  Bumping this in the hope someone has some idea.

---

### Post by tredegar on 2011-02-24
Please plug the drive in, then post the output of the following commands:

```
sudo fdisk -l
mount
cat /etc/fstab
```

---

