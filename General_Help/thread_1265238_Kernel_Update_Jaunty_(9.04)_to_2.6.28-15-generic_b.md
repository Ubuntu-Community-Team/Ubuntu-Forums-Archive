---
title: "Kernel Update Jaunty (9.04) to 2.6.28-15-generic breaks vfat support"
date: 2009-09-13
forum: General Help
---

### Post by arkticcool on 2009-09-13
Before the update the Jaunty would automatically mount all vfat (fat32) USBs that I attached to it. However, after restarting following the kernel update to 2.6.28-15-generic, I get the following error message, (from nautilus I assume).
```

Cannot mount volume.
The volume 'USB' uses the vfat file system which is not supported by your system.
```
When I type into terminal ```
tail -f /var/log/syslog
```Just before plugging in the offending vfat (fat32) system I get the following FATAL EROR from /var/log/syslog, I don't believe the rest is useful.
```

Sep 13 20:22:13 home-desktop modprobe: FATAL: Error inserting vfat (/lib/modules/2.6.28-15-generic/kernel/fs/fat/vfat.ko): Cannot allocate memory 
Sep 13 20:22:13 home-desktop kernel: [32617.952217] vmap allocation failed: use vmalloc=<size> to increase size.

```

How can I resolve this issue?

---

### Post by arkticcool on 2009-09-13
This error does not occur when I use ntfs, but only when I format the usb with fat32/16. However the ntfs filesystem is hardly the best filesystem for any USB - I use both fat32/16 to transfer files between windows/linux computers (no samba).

---

### Post by biinarii on 2009-09-27
i Have the exact same problem, did you manage to fix it?

This is my output :

biinarii@ubuntu-desktop:~$ sudo mount -t vfat /media/HDD01 /dev/sda6
mount: unknown filesystem type 'vfat'
biinarii@ubuntu-desktop:~$ sudo modprobe vfat
FATAL: Error inserting vfat (/lib/modules/2.6.28-15-generic/kernel/fs/fat/vfat.ko): Cannot allocate memory


Anyone??

---

### Post by arkticcool on 2009-09-27
I just retried using my vfat based USBs, and for some reason they work - I don't know how or why - perhaps it just fixed it self after a restart (one does not question the ubuntu gods). I can mount VFAT based USBs under Jaunty with the 2.6.28-15 generic kernel. Just try a restart see if it works - or like me wait a few weeks.

---

