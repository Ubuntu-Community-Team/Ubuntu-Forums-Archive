---
title: "CDRW and DVD-ROM don't work"
date: 2006-03-31
forum: General Help
---

### Post by 12quality on 2006-03-31
All of the sudden, my optical drives just don't work in Ubuntu.  They physically work: they eject and have power and stuff, but CD's and such are no longer detected.

In /dev, there is no hdb or hdc, or cdrom cdrom0 or cdrom1.  I've tried mknod, but have no idea what I am doing with that and it doesn't fix anything.  I've tried to reboot several time to no avail.

Help!

---

### Post by ispmarin on 2006-03-31
Can you post your fstab? Does lspci dmesg shows your dvd/cd driver? sometimes a chmod a+rwx (or 755) on /dev/hdc solves the problem...

---

### Post by 12quality on 2006-03-31
[QUOTE=ispmarin]Can you post your fstab? Does lspci dmesg shows your dvd/cd driver? sometimes a chmod a+rwx (or 755) on /dev/hdc solves the problem...[/QUOTE]

lspic doesn't show the drives, and dmesg doesn't show any errors related to the drives.

The lines in my fstab for the cdroms are
```

/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,auto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,auto  0       0

```

But I have tried changing these to different values like /dev/cdrom.

The problem is there is nothing in /dev related to the drives.  I tried to create them with 
```
sudo mknod -m 0660 /dev/hdb b 22 0
``` and similar things, but nothing works.

---

### Post by 12quality on 2006-04-18
I still haven't received adequate help and I can't use my DVD-rom or CD-rw.

Can someone at least explain how hardware is detected and configured?  Is each device detected on startup or is some original detection stored somewhere.  Is there any automatically configuring that will detect hardware?

---

