---
title: "System Folders? [directory choices during OS install confusion &gt;&lt;]"
date: 2010-10-04
forum: General Help
---

### Post by justing943 on 2010-10-04
Hi everyone! :)

I recently found out about Ubuntu, and wanted to give it a try as it looked good for a non-gamer like me. I stuffed up some partition stuff and had to reformat my whole computer, so now I'm installing from scratch.

Before I do it again though, I'd like to know, which are they 'system' directories [like all the Program Files, User, Windows, and stuff in Windows, just stuff that automatically goes to "C:" drive] and which are 'storage' directories? Because I'd like to store them separately. Also, can my Windows and Ubuntu share the same 'data' directory? By that, I mean just where I chuck all my downloaded stuff.

Thanks,

-Justin :)

---

### Post by ridgeland on 2010-10-06
You'll probably develop some preferences over time but I format my hard drives to have one large Data partition then smaller partitions of 10GB for systems.  On install I tell it to use a 10GB partition for / (system root) and I don't select a different partition for "home" and such.
I keep all my Data in the partition for Data, /etc/fstab mounts it each time I boot.
Windows does not read Linux partitions (by default anyway).  Linux can read Windows partitions.  So if you want to share easily use a NTFS partition for Windows+Linux data.  Both can read and write to it (/etc/fstab settings again).

---

