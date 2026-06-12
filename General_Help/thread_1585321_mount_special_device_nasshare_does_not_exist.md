---
title: "mount: special device //nas/share does not exist"
date: 2010-09-30
forum: General Help
---

### Post by sixtiesman on 2010-09-30
Hi guys :)

I've just upgraded to the new version of Ubuntu (10.04) and I've got a problem with the mounting configuration.

My PC access to a NAS server which is running samba. Everything worked great before upgrading

In the **/etc/fstab**, I added the following line :

```
//nas/share        /mnt/share  auto    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777   0       0
```and the system always replies :

```
mount: special device //nas/share does not exist
```The same occurs if I replace "nas" by the IP address of the machine. Furthermore, the  machines are both pingable.

Can you help me ? Has change happened to the mounting system ?

thanks !

---

### Post by dino99 on 2010-09-30
mountmanager is a nice tool to deal with partitions and devices, install it with synaptic and set your prefs: system admin mountmanager

---

### Post by sixtiesman on 2010-10-03
ok I'll try that tool. Thanks !

---

