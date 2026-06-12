---
title: "Truecrypt + NTFS"
date: 2011-09-02
forum: General Help
---

### Post by la_tristesse on 2011-09-02
Dear Ubuntu Users,

I'm using Truecrypt together with a NTFS formated USB HDD but the Transmission and the VDR User is not able to write to that partition. I already read the tutorials regarding mounting ntfs patitions and its lack of support for linuxs ACL.

This is the commandline I used to mount the USB HDD:

```
$ truecrypt -t --filesystem=ntfs-3g -m nokernelcrypto --fs-options="uid=1000,gid=107,umask=007" --protect-hidden=no /dev/sda1 /media/usb1/
```uid=1000 because thats the user account, I use to access the hdd with samba
gid=107 because thats the group of fuse which has rights to write to /dev/fuse

```
$ mount

truecrypt on /tmp/.truecrypt_aux_mnt1 type fuse.truecrypt (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
/dev/loop0 on /media/usb1 type fuseblk (rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
```I can read and write to hdd with uid 1000. Any suggestions?

---

