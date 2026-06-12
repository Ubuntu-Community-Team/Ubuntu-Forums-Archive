---
title: "Swap fails to mount"
date: 2009-11-04
forum: General Help
---

### Post by noondaysun on 2009-11-04
Hi all.

After a power outage, my Ubuntu 9.10 failed to mount the swap partition at boot.  The OS starts without the swap mounted.  I can manually turn the swap on, but the next time I reboot, the swap will again fail to mount.

Any ideas what is wrong here?

---

### Post by undecim on 2009-11-04
9.10 uses an encrypted swap. Check that the following is in your /etc/fstab```
/dev/mapper/cryptswap1 none swap sw 0 0
```
And the the following is in your /etc/crypttab```
cryptswap1 /dev/sda2 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

---

### Post by noondaysun on 2009-11-04
> **undecim said:**
> 9.10 uses an encrypted swap. Check that the following is in your /etc/fstab```
/dev/mapper/cryptswap1 none swap sw 0 0
```And the the following is in your /etc/crypttab```
cryptswap1 /dev/sda2 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

Thanks undecim

As for my fstab, this is the entire contents of it

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=7eb9cc92-e71e-42f4-8218-09a8960c41e4 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=a5666432-2e71-4372-b067-60c85154f58e /home           ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=1cab0f8c-4d9f-443f-9c1c-6c0e677ad61a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
I have a UUID where you show a path.  

My crypttab file has nothing in it except the header.
> # <target name>    <source device>        <key file>    <options>


---

### Post by undecim on 2009-11-05
I guess encrypted swap is used only when encrypted home directories are used.

Check the UUID of your swap partition against what is in fstab (ls -l /dev/disk/by-uuid)

---

### Post by noondaysun on 2009-11-05
That was it.  The UUIDs didn't match.  I edited fstab and now the swap mounts.

Thanks undecim.

---

### Post by Hilko on 2009-12-07
I had the same problem. I hope this will fix it.
The ls -l command does not show the UUID. I could find it with this command
```
sudo blkid
```

---

