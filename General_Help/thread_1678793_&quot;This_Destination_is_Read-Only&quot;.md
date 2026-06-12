---
title: "&quot;This Destination is Read-Only&quot;"
date: 2011-01-31
forum: General Help
---

### Post by mikmalot on 2011-01-31
My external hard drive has all of a sudden decided that it wants to be read only, meaning I can not add files to it, delete files, or even move them around. WHen I try to check the permissions, I get the error that permissions could not be determined.

I've tried changing permissions through the terminal using "sudo chmod u+w /media/filessystem", but I only get the message back "chmod: changing permissions of `/media/filesystem: Read-only file system".

Thoughts? Suggestions?

---

### Post by mikewhatever on 2011-01-31
If the file system is mounted as read only (may happen due to errors), changing file permissions wouldn't work. You'd have to remount it as wr. On top of that, most external disks are formatted as fat32 or ntfs, the file systems that don't support the Linux permissions.
Look at the output of the **mount** command to figure out if it's mounted as read only. Run the file system check if needed with the Disk Utility.

---

### Post by mikmalot on 2011-01-31
I ran the mount command, and I got this output:

/dev/sdb2 on /media/filesysystem type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

from that output, it looks like it's read-write (that's the rw, correct?). It's also neither fat32 or nfat, as I formatted it in Ubuntu. Finally, I ran file system check and the result came up clean.

---

### Post by mikmalot on 2011-01-31
I guess I should clarify, just in case there's any ambiguity: despite the last post (it appearing to be mounted with r/w capability, and the file check coming up clean), I still get the read only error.

---

### Post by mikmalot on 2011-02-03
Since there seem to be no more suggestions, should I reformat it and hope for the best?

---

### Post by Prescilla on 2012-05-09
> **mikmalot said:**
> Since there seem to be no more suggestions, should I reformat it and hope for the best?
I have the same problem with my USB flash drive.
I run mount from the terminal and it is clearly rw filesystem, but I cannot copy files to it nor delete files from it.
Is there another option besides formatting the drive? I have important data on it and I really need to keep it.

---

