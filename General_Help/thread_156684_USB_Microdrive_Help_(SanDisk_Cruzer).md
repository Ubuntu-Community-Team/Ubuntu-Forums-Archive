---
title: "USB Microdrive Help (SanDisk Cruzer)"
date: 2006-04-07
forum: General Help
---

### Post by Mortuis on 2006-04-07
I'm having trouble getting Ubuntu to talk to my USB Microdrive (SanDisk Cruzer).

I use a USB mouse, and have only one port open on my docking station.  I unplug the mouse, then plug in the Microdrive, go to Places -> Computer and see that it's there listed as "SanDisk Cruzer Micro".  When I try to open it though, I get an error message telling me:

"**Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.**"

When I expand details it says:
"[B]mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount[/B]"

So I try the dmesg | tail command and get:
"[B]john@uriel:~$ dmesg | tail
[4359304.131000] VFS: Can't find ext3 filesystem on dev sda.
[4359304.141000] VFS: Can't find ext3 filesystem on dev sda.
[4359304.150000] VFS: Can't find an ext2 filesystem on dev sda.
[4359304.160000] VFS: Can't find an ext2 filesystem on dev sda.
[4359304.181000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4359304.201000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4359304.214000] XFS: bad magic number
[4359304.214000] XFS: SB validate failed
[4359304.228000] XFS: bad magic number
[4359304.228000] XFS: SB validate failed[/B]"

I checked the filesystem under windows and XP said that the Microdrive was using the FAT filesystem.

Anyone know how to resolve this?

---

### Post by Mortuis on 2006-04-10
Well looking around some more on google last night I found a solution:
**mount -t vfat /dev/sda1 /mnt/usb**

Does anyone know if there's a way I can tell ubuntu to try sda1 when sda fails to mount so that this can be done automatically rather than having to do it manually.

At least there's a fix, though. :-)

---

### Post by jandi on 2006-04-22
I have the same problem.  The USB was working fine before, but now, it's unable to automount any flash units.   

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

dmesg | tail

[4294873.397000] VFS: Can't find an ext2 filesystem on dev sda.
[4294873.443000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4294873.452000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4294873.865000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4294873.865000] SGI XFS Quota Management subsystem
[4294873.869000] XFS: bad magic number
[4294873.869000] XFS: SB validate failed
[4294873.879000] XFS: bad magic number
[4294873.879000] XFS: SB validate failed
[4294873.913000] JFS: nTxBlock = 8094, nTxLock = 64758

I tried to manually mount the drive
mount -t vfat /dev/sda/ /mount/usb
and came up with same errors

Tried it with sda1, and it worked.   Is there a way to automatically try to mount sda1?   This is so odd, as this used to work before, but I don't remember changing much in my system ever since, other than installing latest updates.

---

### Post by erbedo on 2006-04-22
You can try this:
```
sudo ln -s /dev/sda1 /dev/sda
```

---

### Post by jandi on 2006-04-22
Thanks for the suggestion, that sounds pretty logical.

It's working now, yes!!!

For some reason, permissions for hal were screwed up, so I set them, restarted the computer,  and now automount works again.

:mrgreen:

---

### Post by erbedo on 2006-04-22
:) I didn't know if there's a faster way to do that :)

---

