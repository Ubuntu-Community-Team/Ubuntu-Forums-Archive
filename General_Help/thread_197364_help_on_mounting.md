---
title: "help on mounting"
date: 2006-06-15
forum: General Help
---

### Post by koda on 2006-06-15
hi!
I was trying to mount my sdb1 partition but i receive this output
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
and if I do dmesg | tail 
```
[4302282.524000] NTFS-fs error (device sdb1): ntfs_attr_find(): Inode is corrupt.  Run chkdsk.
[4302282.525000] NTFS-fs error (device sdb1): ntfs_read_inode_mount(): Failed to lookup attribute list attribute. You should run chkdsk.
[4302282.525000] NTFS-fs error (device sdb1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[4302282.525000] NTFS-fs error (device sdb1): ntfs_fill_super(): Failed to load essential metadata.

```

the partition is a ntfs RAID5 software.

any ideas about how to mount it? :confused: 
thanks!
Koda

---

### Post by ifokkema on 2006-06-15
[QUOTE=koda]hi!
I was trying to mount my sdb1 partition but i receive this output
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
and if I do dmesg | tail 
```
[4302282.524000] NTFS-fs error (device sdb1): ntfs_attr_find(): Inode is corrupt.  Run chkdsk.
[4302282.525000] NTFS-fs error (device sdb1): ntfs_read_inode_mount(): Failed to lookup attribute list attribute. You should run chkdsk.
[4302282.525000] NTFS-fs error (device sdb1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[4302282.525000] NTFS-fs error (device sdb1): ntfs_fill_super(): Failed to load essential metadata.

```

the partition is a ntfs RAID5 software.

any ideas about how to mount it? :confused: 
thanks!
Koda[/QUOTE]

I assume this has worked before? Did you try booting into windows and run a checkdisk on this drive? The error logs says it's bad.

---

### Post by koda on 2006-06-16
I've tried what you suggested but it failed to mount just the same as before :( 
and i did a complete scandisk! :-( 
Can't understand why it fails!!!
Koda

---

### Post by scxtt on 2006-06-16
have you tried:

[indent]sudo mount -t ntfs /dev/sdb1 /"where you want to mount it"[/indent]

---

### Post by koda on 2006-06-16
[QUOTE=scxtt]have you tried:

[indent]sudo mount -t ntfs /dev/sdb1 /"where you want to mount it"[/indent][/QUOTE]
well... yes, the output i wrote in my first message was right the output of this command :rolleyes: :rolleyes: :rolleyes: 

i looked around some guides and found out that there are problem with the Intel Matrix Storage Software RAID and linux... is that true? Since I have an hardware controller, do you suggest me to move the array there?

thanks
Koda

---

### Post by scxtt on 2006-06-16
i have support for a hardware raid (0/1) on my MB - i setup a RAID 0 array, but when installing ubuntu w/ the Alternate disk it was still recognized as two separate disks, so i gave up (could have done a software RAID, but didn't feel like it) ...

---

