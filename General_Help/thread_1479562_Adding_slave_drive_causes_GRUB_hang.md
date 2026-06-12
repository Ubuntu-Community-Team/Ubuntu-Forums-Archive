---
title: "Adding slave drive causes GRUB hang"
date: 2010-05-10
forum: General Help
---

### Post by Cal27 on 2010-05-10
I'm attempting to dual boot Ubuntu and Windows. I've managed to get Windows 7 installed to a separate drive from Ubuntu, but now my computer hangs before starting GRUB.
I had a SATA drive with ubuntu on it and an IDE for storage before. I added another IDE drive for windows on the middle of the cable with the other one. Whenever I have that drive in, my computer hangs. It will boot fine without it.
Any help is greatly appreciated. Thanks.

---

### Post by skibum3027 on 2010-05-10
To clarify, your hard drive configuration is:

sda-> Ubuntu
hda-> Storage
hdb-> Windows

And the computer hangs anytime hdb is plugged in? This sounds like grub isn't loading when the windows drive is plugged in. Is that correct?

output of ```
df -h
``` would be helpful :)
Are you running grub2?

---

### Post by Cal27 on 2010-05-10
Yes, except all the drives are sd*, so it's:
sda -> Ubuntu
sdb -> Storage
sdc -> Windows

df -h:
```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1007M  2.4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M  2.4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  108K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  172K 1007M   1% /dev
tmpfs                1007M   76K 1007M   1% /dev/shm
rootfs               1007M   22M  986M   3% /
/dev/sr0              699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1007M   12K 1007M   1% /tmp

```sudo fdisk -l, with some stuff trimmed out
```

Disk /dev/sda: 80.0 GB
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```
Ooh. Maybe the boot flags on sdb1 and sdc1 are contributing or causing the problem...

And I'm using grub legacy.

---

### Post by Cal27 on 2010-05-12
Okay, now when I attempt to start my computer with all hard drives attached, it says:
```

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

```
But if I get rid of the windows drive, Ubuntu will start up with no problems.

---

