---
title: "how to set default mount option of USB hdd"
date: 2010-03-25
forum: General Help
---

### Post by unknown3 on 2010-03-25
i am using ubuntu 9.10 x64 version

when i plug a USB hdd, it is auto mounted

from the log:

Mar 21 06:34:23 universe ntfs-3g[5066]: Version 2009.4.4 external FUSE 27
Mar 21 06:34:23 universe ntfs-3g[5066]: Mounted /dev/sdd (Read-Write, label "xxx", NTFS 3.1)
Mar 21 06:34:23 universe ntfs-3g[5066]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Mar 21 06:34:23 universe ntfs-3g[5066]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,[COLOR=Blue]relatime[/COLOR],fsname=/dev/sdd,blkdev,blksize=4096

I want to set the default mount option to "noatime, nodiratime", but where can i set it?

I know i can do this in fstab, but i do not want to add lot of entries there

---

### Post by unknown3 on 2010-03-28
anyone can help?

---

### Post by drs305 on 2010-03-28
Try setting them in gconf-editor. Use "gksu" if you want to make it universal, or omit it if you just want the settings to apply to your username only.

```
gksu gconf-editor /system/storage/default_options/ntfs-3g/mount_options
```

This setting doesn't exist in Lucid but I believe this is the entry for previous versions.

---

### Post by unknown3 on 2010-03-28
> **drs305 said:**
> Try setting them in gconf-editor. Use "gksu" if you want to make it universal, or omit it if you just want the settings to apply to your username only.

```
gksu gconf-editor /system/storage/default_options/ntfs-3g/mount_options
```This setting doesn't exist in Lucid but I believe this is the entry for previous versions.

I am using Ubnutu x64 9.10, i cannot found the key

---

### Post by drs305 on 2010-03-28
> **unknown3 said:**
> I am using Ubnutu x64 9.10, i cannot found the key

I loaded a VM of 9.10 and did not find it either. You can create the key with the following command. I cannot guarantee that it will solve your issue however. 

```

gconftool-2  -t list --list-type=string -s /system/storage/default_options/ntfs/mount_options "[noatime,nodiratime]"

```

To put it into root's config, run it with "sudo".

---

### Post by unknown3 on 2010-03-29
> **drs305 said:**
> I loaded a VM of 9.10 and did not find it either. You can create the key with the following command. I cannot guarantee that it will solve your issue however. 

```

gconftool-2  -t list --list-type=string -s /system/storage/default_options/ntfs/mount_options "[noatime,nodiratime]"

```To put it into root's config, run it with "sudo".

thx for your help, but this do not work

from google, this setting is for hal, but ubuntu 9.10 use udev instead

---

