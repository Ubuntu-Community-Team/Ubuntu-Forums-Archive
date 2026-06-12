---
title: "How do I sync /home for both fat/thin client"
date: 2010-08-10
forum: General Help
---

### Post by jeight on 2010-08-10
[SIZE=3]I have a LTSP server with a fat client chroot. I use LTSP_FATCLIENT=False to run the older computers in a thin client enviroment.

How do I sync the /home directories of the server /home and the chroot for my fat clients. If I log into a fat client system I have a /home in the chroot. If I log into a thin client computer the /home is in the server. I need a way to either sync the two  or redirect one /home to the other.[/SIZE]

---

### Post by jeight on 2010-08-10
[SIZE=2]I had it backwards. It is much easier to use [/SIZE][SIZE=3][SIZE=2]LTSP_FATCLIENT=true in a thin client enviroment or use local_apps instead. I'm still learning but I hope it helps someone else in the future.

[/SIZE][SIZE=2]Then use these modifications in you /var/libtftpboot/ltsp/i386 file.
LOCAL_APPS = True
MOUNT_LOCAL_REAL_HOME = True

read [https://help.ubuntu.com/community/UbuntuLTSP/GetMoreFromLocalApps](https://help.ubuntu.com/community/UbuntuLTSP/GetMoreFromLocalApps) for help getting local_apps working.[/SIZE]
[/SIZE]

---

