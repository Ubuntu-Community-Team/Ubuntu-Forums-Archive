---
title: "Grub2 not showing winxp..."
date: 2009-12-30
forum: General Help
---

### Post by emigrant on 2009-12-30
hi all,
im dual booting winxp with karmic. i accidently deleted the ntldr and had it restored  later.
but now, the grub2 not showing winxp at startup.

what is the solution.


thank you very much.

PS: some info:

```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```


```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed73ed73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       19457   120447337+   f  W95 Ext'd (LBA)
/dev/sda5            4463        8286    30716248+   7  HPFS/NTFS
/dev/sda6            8287       12110    30716248+   7  HPFS/NTFS
/dev/sda7           12111       13640    12289693+   7  HPFS/NTFS
/dev/sda8           13641       13665      200781   82  Linux swap / Solaris
/dev/sda9           13666       19457    46524208+  83  Linux

```

---

### Post by emigrant on 2009-12-30
hi guys,
sorry for the trouble.problem solved.

---

