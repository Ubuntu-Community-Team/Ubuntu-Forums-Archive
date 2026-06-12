---
title: "how does ubuntu know where to find home ?"
date: 2006-02-25
forum: General Help
---

### Post by soonindallas on 2006-02-25
I just moved all my /home files into a newly created /home partition and spent a whole day fixing the permissions error with .dmrc to get back in...  but I still have some more partitioning work to do.  this will involve moving my /home which is mounted as /dev/hda3

if the partition number gets changed, how can I tell ubuntu where to look for the home partition ?

I saw a file /proc/mounts which looks like this on my box:
```

rootfs / rootfs rw 0 0
none /dev ramfs rw 0 0
/dev/hda6 / ext3 rw 0 0
/dev/hda6 /dev/.static/dev ext3 rw 0 0
proc /proc proc rw,nodiratime 0 0
sysfs /sys sysfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw 0 0
/dev/hda3 /home ext3 rw 0 0
/dev/hda1 /media/hda1 vfat rw,nodiratime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/hda2 /media/hda2 vfat rw,nodiratime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/hda7 /media/hda7 ext3 rw 0 0
```

if the partition number gets changed, can I just edit this (actually the target, as /proc/mounts is a link) to point to the right one ?

I noticed that grub only tells the kernel where to find the / partition.

Is there an entre to make to the partition table for a linux /home partition ?

---

### Post by Xian on 2006-02-25
[QUOTE=soonindallas]if the partition number gets changed, how can I tell ubuntu where to look for the home partition ?[/QUOTE]

In your /etc/fstab file. Example:

```

/dev/hda7     /home      ext3    defaults      1 2

```

---

### Post by soonindallas on 2006-02-25
thanks.

so I should just edit /etc/fstab if this goes awry ?

---

### Post by Xian on 2006-02-25
[QUOTE=soonindallas]so I should just edit /etc/fstab if this goes awry ?[/QUOTE]

Unless your /home directory is on the same partition as root you will always want to have it included as a mount point in your fstab file. That is the method used to access that partition during the boot sequence.

---

### Post by soonindallas on 2006-02-26
thanks.  this helped me a lot.

---

