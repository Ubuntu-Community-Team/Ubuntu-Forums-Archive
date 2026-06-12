---
title: "Filesystem over multiple files"
date: 2011-12-14
forum: General Help
---

### Post by iceman on 2011-12-14
Hello world,

Main Purpose:
I would like to build a filesystem splitted in different files.

I was able to build a filesystem like this, but i found a limit unfortunately:

a=0;while [ $a -lt 8 ]; do dd if=/dev/zero of=DISK$a bs=1M count=100; let a=a+1; done
a=0;while [ $a -lt 8 ]; do sudo losetup /dev/loop$a DISK$a; let a=a+1; done

In this way i create 8 100M files and mount all as loop
After that, i can create a RAID0 (by mdadm) of all:
sudo mdadm --create /dev/md0 --level=0 /dev/loop0 /dev/loop1 ..............
And then i can format and mount device /dev/md0

Anyway, the limit is loopdevice, because it's possible to have at least 8 lodevice.
Is there a way to have a filesystem splitted in different "piecies"? (with or without lodevices...)
There's no problem about using mdadm or LVM or somethingelse... i only want a single filesystem over multiple files (filesize is not important...)

Please, let me know if you have any idea...

---

### Post by iceman on 2011-12-15
Noone?
Is it so difficult?

:confused:

---

