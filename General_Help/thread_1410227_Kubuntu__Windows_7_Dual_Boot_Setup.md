---
title: "Kubuntu / Windows 7 Dual Boot Setup"
date: 2010-02-18
forum: General Help
---

### Post by Pablo173 on 2010-02-18
I just bought a Dell 537s machine and configured it for dual boot of Windows 7 and Kubuntu 9.10.

On my old dual boot machine I had the Windows System and the Linux System on different disk partitions.  That way I could write fstab in such a way as to make the Windows System read-only as seen from Linux, so Linux couldn't mess up any Windows System files (and since Windows can't read ext3, Windows couldn't mess up the Linux System).

But the new machine came with Windows 7 installed and gobbling up 3 primary partitions.  Kubuntu installed itself in such a way that Linux can read/write to the Windows System.  This makes me nervous that Kubuntu might be able to mess up Windows 7.

Is there any way to make specific Windows 7 directories/files unwriteable as seen from Linux without altering their behavior in Windows 7?

Thanks in advance.

---

### Post by graphius on 2010-02-19
I would guess that one of the partitions is a "recovery partition" don't mount this one. Other than that, I have never had a problem with linux "messing up" a windows install. Unless you specifically write to the drive linux won't touch the partition.
If you desire, you could set up the mount in fstab as read only, but then it is a pain if you want to transfer files between the two programs (windows and linux).
I actually mapped my document, picture, music, etc files to the win7 My Documents equivalents. It works for me...

---

