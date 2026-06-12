---
title: "Automatically unmount encrypted USB flash drive when device is unplugged"
date: 2010-04-21
forum: General Help
---

### Post by Despot on 2010-04-21
I formatted the USB flash drive using Karmic's Format Disk utility (right-click on a volume, select "Format..."), and selected "Encrypted, compatible with Linux (FAT)" from the "Type" drop-down menu.

It mounts correctly when I plug it in, and I can access the files just fine. When I unplug the Flash drive without using the 'Safely Remove Drive' option, the icon on my desktop changes its name to '2.0 GB Encrypted', instead of disappearing and unmounting like my unencrypted Flash drives do.

I would like to have encrypted Flash drive treated in the same way as my unencrypted Flash drives, which disappear and unmount when unplugged, even if the 'Remove Safely' menu option isn't used. What can I do to accomplish this?

NOTES:
When I plug the encrypted Flash drive in, the following line shows up in the output of 'mount'. 'secure' is the name I gave the disk during the format process:

```
/dev/mapper/devkit-disks-luks-uuid-302db16c-c6e2-4dd9-a259-436437c76475-uid1005 on /media/secure type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1005,gid=544,shortname=mixed,dmask=0077,utf8=1,flush)

```
The disk shows up on my desktop with the name 'secure'.

When I unplug the device, 'mount' still shows this line:

```
/dev/mapper/devkit-disks-luks-uuid-302db16c-c6e2-4dd9-a259-436437c76475-uid1005 on /media/secure type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1005,gid=544,shortname=mixed,dmask=0077,utf8=1,flush)
```

The drive's contents can still be viewed in Nautilus, but I can't open files.

---

### Post by SnickerSnack on 2010-04-21
Not an answer to your question:

I think you _really_ should unmount drives before removing them.  It's there for a reason.

---

