---
title: "Grub 2 Configuration Problem"
date: 2009-12-22
forum: General Help
---

### Post by ChrisB111 on 2009-12-22
When I select my kernel in grub 2 it gives me the "out of disk" error. I can boot manually using these commands but I would like to fix grub. However I have no idea how to.

Thanks,

Chris

```
set root=(hd0,7)
linux /vmlinuz root=/dev/sdb7
initrd /initrd.img
boot
```

```
chris@chris-desktop:~$ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe655fbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ebf41fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6438    51713203+   7  HPFS/NTFS
/dev/sdb2            6439       19457   104575117+   5  Extended
/dev/sdb5            6439       12817    51239254+  83  Linux
/dev/sdb6           12818       13003     1494013+  82  Linux swap / Solaris
/dev/sdb7           13004       19187    49672948+  83  Linux
/dev/sdb8           19188       19457     2168743+  82  Linux swap / Solaris
```

---

### Post by kingkongmok on 2009-12-22
Maybe you could update your grub2 config file "grub.cfg" after your login. Like this:
sudo update-grub2

---

