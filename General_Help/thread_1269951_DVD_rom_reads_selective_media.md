---
title: "DVD rom reads selective media"
date: 2009-09-18
forum: General Help
---

### Post by daimyo505 on 2009-09-18
I am trying to get my DVD-rom(s) to read DVDs but I am having a really hard time finding out what is wrong. I recently replaced a really old DVD burner in my computer with a newer one. The old one would not read any discs: commercial DVD/CD, burned or unburned DVD/CD, data, music or video. That DVD burner was probably 6 years and had worked for a long time. I replaced it with another DVD burner I had lying around.

The new one will read data DVD/CD, unburned DVD/CD, but no movie DVDs. Any help is appreciated. Thanks!

Ubuntu 9.04

I've all the software sources checked: main, universe, restricted, multiverse

"sudo apt-get install libdvdcss2"
gets me
"libdvdcss2 is already the newest version."

Here is my fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e8e78e5f-7fb5-4c5e-8519-9e3df80055cf /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=f62ec01a-1478-4b9c-b3bd-031a29d976f2 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=df545348-390d-4822-8ab9-196bbd8bd970 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

