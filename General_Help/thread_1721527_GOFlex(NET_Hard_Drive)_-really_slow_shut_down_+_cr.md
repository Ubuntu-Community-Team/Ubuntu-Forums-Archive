---
title: "GOFlex(NET Hard Drive) -really slow shut down + crushes when used with torrent"
date: 2011-04-04
forum: General Help
---

### Post by deckoff on 2011-04-04
Ok
I bought and installed Seagate GoFlex Net Drive. It is auto mounted in /etc/fstab with :

```

//192.168.1.110/GoFlex\040Home\040Public /media/SG-PUBLIC cifs username=***,password=***,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```
I experience very slow log off and shut down, + problems when trying to download torrents directly to the drive:( Any ideas how to fix it - unmount at shut down, or else? I also have problems when coping files to the drive when using the system with Kubuntu (Ubuntu is ok with the same fstab file on the same machine)

---

### Post by deckoff on 2011-04-08
Here is the answer to my question
1) Slow shut down is a result of a Ubuntu bug
2) Torrent freezes are result of a kernel bug, which is fixed in newer kernels. vers=3 shoud be added to fstab
3) noperm should be added to fstab to fix permission error in Kubuntu

---

