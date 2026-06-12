---
title: "all my .rtf files now have execute permission"
date: 2010-05-17
forum: General Help
---

### Post by noob555 on 2010-05-17
Hello all,

A bunch of my .rtf files suddenly (within the last few days, not sure when) have the "Allow Executing File as Program" box checked under their file Permissions.  So whenever I try to open an rtf document, it asks if I want to run it.  

What's up with that?  I can't think of anything I've done that would do that.

And how do I get it to stop?

---

### Post by parn on 2010-05-17
Did you copy those files from Windows (directly or via usb)?

In any case, just open terminal, go to the folder where u store your .rtf file and type:
chmod 644 *.rtf

---

### Post by noob555 on 2010-05-17
> **parn said:**
> Did you copy those files from Windows (directly or via usb)?

In any case, just open terminal, go to the folder where u store your .rtf file and type:
chmod 644 *.rtf
Hmmmm, I don't recall.  It's been awhile since I really looked at these files.

Thanks for the help.

---

### Post by srs5694 on 2010-05-17
Where are they stored? If they're stored on a FAT, NTFS, or other non-Linux/non-Unix filesystem, then the permissions are most probably assigned via mount-time options. You can fix the issue by creating or editing an /etc/fstab entry for the partition and setting appropriate permissions in an option there. If the files are stored on an ext2fs, ext3fs, ext4fs, ReiserFS, JFS, XFS, Btrfs, or other Linux filesystem (or even most non-Linux but Unix filesystem, such as HFS+), then the execute permission most probably got there by an accidental use of chmod or some GUI equivalent. You can remove them the same way, as in "chmod a-x foo.rtf"; however, doing this en masse might take some finesse, since you should *not* remove it from all your files and directories. Among other things, the execute permission must be present on most directories for them to function correctly.

---

