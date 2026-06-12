---
title: "Dual booting and shared partition problems"
date: 2011-12-09
forum: General Help
---

### Post by atom94 on 2011-12-09
I've just got a new laptop and installed Ubuntu 11.10 64 bit, dual booted with Windows 7 Professional (32 bit). I have four partitions - a 50GB NTFS partition for Windows, a 20GB Ext4 partition for Ubuntu, a 390GB NTFS shared partition for documents, and 3GB of swap space. I have changed /etc/fstab so that the documents partition is mounted automatically at startup:

```
/dev/sda3   /media/Documents   ntfs   auto   0   1
```

Whenever I boot Ubuntu, I get a message saying *Serious errors where found while checking the disk drive for /media/Documents. Press I to ignore, S to skip mounting, or M for manual recovery.* On my previous system I was dual booted with Windows XP and Ubuntu 11.04 (32 bit), and didn't have any problems. /etc/fstab was set up exactly the same.

---

### Post by LewisTM on 2011-12-09
This is a message that typically says Ubuntu is unable to mount the filesystem for some reason. For instance it could fail a consistency check.

Can you manually mount the partition?
```
sudo mount /dev/sda3
```

If you can then you may want to simply set the last digit of the fstab entry to 0 instead of 1, to disable automatic check at boot time. You can perform those disk checks in Windows.

---

### Post by atom94 on 2011-12-09
If I press I on the error screen the file system mounts OK, and all my files are there as far as I can tell. I have also run checkdisk in Windows, which hasn't found any problems.

---

### Post by oldfred on 2011-12-09
Your last digit is 1, which is used by Linux to know if or when to run filechecks. But Linux cannot run chkdsk so it says it is a problem. Change to 0 since you cannot run file checks from Linux, but remember to run chkdsk regularly.

From 
man fstab

>        The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.

These are settings I have seen recommended, note all have 0 as last setting:
What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0
EDIT: If you prefer to be the owner then you can also go with this:
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,uid=1000,windows_names 0 0
Hide windows mount with noauto:
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

---

### Post by atom94 on 2011-12-09
I know what you mean about setting fs_passno to 0. i'm just wondering why it worked on my old setup with the exact same settings.

---

