---
title: "davfs - losing data/cache"
date: 2010-05-25
forum: General Help
---

### Post by rabby_ on 2010-05-25
Hi,

Setting up davfs went properly and i stored the host/user/pw in the secrets to avoid input request any time when mounting.
If i mount from gui/gnome/desktop as user, all seems to work: it mounts, allows me to write data to the medium and on unmounting the data is uploaded/stored to the webdav.

However, i would like to auto-mount the webdav as device. That's why i added this line to the /etc/fstab
> [https://sd2dav.1und1.de/](https://sd2dav.1und1.de/)        /backup         davfs   rw,user,auto,gid=users       0       0
*mount /backup* has no problem and now i try to copy any file to this directory. After, I *umount /backup* and it says: > umount.davfs: wait until files in cache are saved .. OK after some seconds.

Alright, and now i *mount /backup* again and there is none of the files there which i copied to this mountpoint before :-(
Any changes are undone and all data is lost whenever i work with the webdav and mount+umount.

May someone tell me what might be going wrong here? 
Furthermore, isn't there any log file for mount.davfs? It doesn't tell me any error...

Thanks

---

### Post by dino99 on 2010-05-25
dont know about webdav but it seem to be rights related

maybe mountmanager can help a little

---

