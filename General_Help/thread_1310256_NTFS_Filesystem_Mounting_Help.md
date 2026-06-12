---
title: "NTFS Filesystem Mounting Help"
date: 2009-11-01
forum: General Help
---

### Post by uv_goth on 2009-11-01
I followed instructions here:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I added a line to etc/fstab:

/dev/sda3     /files   ntfs-3g ro,auto,user,fmask=0111,dmask=0000 0       0

I can see the files and access them but it's read-only. Checked permissions and it's 777 with root as owner and group.

Tried rw not ro in fstab to no avail. Any help or helpful links welcome as can't use my main files on separate partition currently.

---

### Post by pastalavista on 2009-11-01
Install 'pysdm' Storage Device Manager to set the mount attributes correctly. It will be found in the System--> Administration menu.

edit: I don't know where it will be in KDE menus. Just use Alt-F2 and run pysdm

---

