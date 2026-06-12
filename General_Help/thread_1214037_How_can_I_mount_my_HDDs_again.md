---
title: "How can I mount my HDDs again?"
date: 2009-07-15
forum: General Help
---

### Post by matamoscas on 2009-07-15
Not really aware of what I was doing, I right-clicked two additional HDDs I had in the left "places" panel of Dolphin, and I selected something like "hide" or something like that -- because i thought if I wasn't using them regularly, they should just be ignored.

Well, a few days later, now I wanted to access them, how can I remount them? 

I simply cannot find any simply answer (or hard one's for that matter).

Thanks in advance

Matteo

here is some additional info when i type "sudo fdisk -l"
e@KubuntuBox:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bad7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7        2438    19535040   83  Linux
/dev/sda3            2439       72960   566467965   83  Linux
/dev/sda4           76610       77825     9767520   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabb0abb0

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000dd5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   83  Linux


Do I just add the information manually to the /etc/fstab file?

I was wondering if there was a nicer, GUI option, just like the one to "right-click" and make them go away =)


figured it out. Duh=)

Not super intuitive, but cool nonetheless =) Right click in the same panel, and select show all entries.

---

