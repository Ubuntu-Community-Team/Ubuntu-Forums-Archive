---
title: "Disable fsck check on External Drive at boot"
date: 2010-06-27
forum: General Help
---

### Post by jamesrl on 2010-06-27
I have an external drive that I like to include in fstab, but I don't want to slow down my boot when the drive is not present.  Right now my computer doesn't boot until I press S, which is annoying.  (Especially when you want to reboot via ssh, and the system freezes until you manually go there.)

Currently the line in fstab is:
```

UUID=abcdefgh-d52c-484e-ab26-d47fabcdefgh /mnt/usb_500gb  ext3    defaults,user  0   0

```

I thought that the last 0 in the sixth column should prevent fsck from checking this drive during boot.  From man fstab:
>        The sixth field, (fs_passno), is used by the fsck program to determine the order in which filesystem checks are  done  at  reboot
       time.   The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.  Filesys&#8208;
       tems within a drive will be checked sequentially, but filesystems on different drives will be checked at the same  time  to  utilize
       parallelism  available in the hardware.  If the sixth field is not present or zero, a value of zero is returned and fsck will assume
       that the filesystem does not need to be checked.


Suggestions?  Never had this problem before lucid.

---

### Post by dcstar on 2010-06-28
> **jamesrl said:**
> I have an external drive that I like to include in fstab, but I don't want to slow down my boot when the drive is not present.
.......


Use the fstab option that does not mount automatically, then the system will not try to mount something that does not exist.

---

### Post by jamesrl on 2010-06-28
Wow.  I swear I checked man fstab reasonably well but I guess I always missed the "nobootwait" option.  My bad; Thanks for your help.

```
UUID=abcdefgh-d52c-484e-ab26-d47fabcdefgh /mnt/usb_500gb  ext3    defaults,user,nobootwait  0   0
```

---

