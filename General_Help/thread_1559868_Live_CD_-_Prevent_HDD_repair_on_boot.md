---
title: "Live CD - Prevent HDD repair on boot"
date: 2010-08-24
forum: General Help
---

### Post by SuperDuckk on 2010-08-24
Hello,

I downloaded ubuntu desktop to use it as a live CD to rescue a dying NTFS disk by clonning it with ddrescue. But I read somewhere it tries to repair corrupt disks during boot. Physically damaged drives shouldn't be written on.

How can I prevent it to scan / repair my damaged drive during boot?

The partition still looks as NTFS and can be read mostly, so will it try to repair even an NTFS partition by default?

Thank you!
Duck

---

### Post by brr872002 on 2010-08-24
> **SuperDuckk said:**
> Hello,

I downloaded ubuntu desktop to use it as a live CD to rescue a dying NTFS disk by clonning it with ddrescue. But I read somewhere it tries to repair corrupt disks during boot. Physically damaged drives shouldn't be written on.

How can I prevent it to scan / repair my damaged drive during boot?

The partition still looks as NTFS and can be read mostly, so will it try to repair even an NTFS partition by default?

Thank you!
Duck

I think ddrescue is for only extended file system or fat16 ,32 it will not work with NTFS.
PL. try to repair attaching it with windows mechine is best option.

---

### Post by SuperDuckk on 2010-08-24
Thanks for your reply BRR. From what I see, it's common to rescue NTFS using ddrescue, as it sees the partition as a binary block, the file system doesn't matter.

FYI:
After having trouble with some recovery software which have their own bootable media, I wanted to see the drive under windows once again, to see if there is a problem with its servos. So I already took a look over it on Windows. Before attaching the drive, I disabled chkdsk (which would further corrupt the disk trying to repair it), disabled search indexing, and thumbnail creation. But windows even writes on the drive when you mount it, and there are also parts like NTFS log etc, which are always written on by Windows. So it was a dangerous move. Even then, I was unable to copy folders because of NTFS permissions, and I don't want to make a heavy write operation to modify all file/folder permissions. And a windows software, 'partition wizard' failed to copy the partition telling me NTFS structure had errors. I was unable to find a way to bypass NTFS permissions under windows.

---

