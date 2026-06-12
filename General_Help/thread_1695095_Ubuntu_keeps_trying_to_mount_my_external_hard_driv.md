---
title: "Ubuntu keeps trying to mount my external hard drive at boot up"
date: 2011-02-25
forum: General Help
---

### Post by daldude on 2011-02-25
Every time Ubuntu boots it tries to mount my external had drive during boot up I get a message on the screen saying Ubuntu can't mount it because it is not ready or not available with the option to press S to skip mounting it or M for manual recovery so I hit S to skip trying to mount it. If I turn it on during boot an allow Ubuntu to mount it then I can't select Safely Remove drive to un mount it after Ubuntu finishes booting because I get the message  "Failed to eject media; one or more volumes on the media are busy"  even though nothing is accessing the drive, I have no open windows of any folders of the drive and no programs are accessing it. I launched the NTFS configuration tool and removed the check mark next to the listing for my external drive but that did not fix the problem.

How do I fix this problem and prevent Ubuntu from trying to mount my external hard drive at boot up?

Thanks

---

### Post by dino99 on 2011-02-25
either remove it from /etc/fstab, or use mountmanager

---

### Post by seawolf167 on 2011-02-25
Aye, remove it from /etc/fstab should do the trick

```
sudo gedit /etc/fstab
```

find the offending entry and delete it, then save and exit

---

### Post by daldude on 2011-02-26
Both these sugestions did not seem to work, first I tried editing the fstab file but Ubuntu still mounted my external drive at boot up requiring it to be on in order for my Ubuntu to finish booting, when I used boot manager it screwed up the fstab file and I could no longer mount my Windows XP Data NTFS partition but I was smart enough to backup the fstab file by saving it as fstab.old and now Ubuntu no longer tries to mount my external drive at boot up but I can still access it by turning it on after booting Ubuntu and I can also unmount it safely. So some how I fixed my problem.:)
Thanks

---

