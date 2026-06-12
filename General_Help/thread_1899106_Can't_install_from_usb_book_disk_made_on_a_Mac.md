---
title: "Can't install from usb book disk made on a Mac?"
date: 2011-12-22
forum: General Help
---

### Post by j0hn_d()e on 2011-12-22
Made a boot disk on a mac. Trying to install it on a NTFS formatted but blank drive that was an old Dell Optiplex. Won't boot. I did it before from Startup Disk Creator in Ubuntu, but it's not working from the mac.  Is there any other way I can make it?

---

### Post by jjex22 on 2011-12-22
Hi there! when you say start up disk, do you mean creating a linux usb installer? if so, try out [unetbootin]("http://unetbootin.sourceforge.net/") if this doesn't support the OS you are trying copy, you can try restoring from disk utility (set partition table as mbr) or using the command

```

dd if=path to iso of=path to usb

```
to get the paths, just drag and drop into terminal.


if you are trying to create a start up disk for mac, have a look at this guide [ehow guide]("http://www.ehow.com/how_5880636_create-startup-disk-os-x.html") however you can't use this to install osx on the laptop.

Hope it helps!

---

### Post by wildmanne39 on 2011-12-22
Hi, also you say > Trying to install it on a NTFS formatted but blank drive ubuntu can not be installed on a NTFS partition it needs to be ext3 or ext4 or some other linux partition.
Thanks

---

