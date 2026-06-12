---
title: "virtualbox: windows to ubuntu file sharing?"
date: 2011-01-28
forum: General Help
---

### Post by abhilashm86 on 2011-01-28
I've installed windows7 on my computer, then ubuntu 10.04 is running as virtual using sun virtualbox. 

I did these methods to share file from windows7. Made network mode to Bridge in settings, Shared Disk C to everyone, then started virtualbox,in ubuntu - opened up nautilus window browser, then in location url

smb://192.168.x.xx 

I gave this url and when i gave password, its not working?? 

Why is this error? how to resolve?

---

### Post by metalf8801 on 2011-01-28
> **abhilashm86 said:**
> I've installed windows7 on my computer, then ubuntu 10.04 is running as virtual using sun virtualbox. 

I did these methods to share file from windows7. Made network mode to Bridge in settings, Shared Disk C to everyone, then started virtualbox,in ubuntu - opened up nautilus window browser, then in location url

smb://192.168.x.xx 

I gave this url and when i gave password, its not working?? 

Why is this error? how to resolve?

Have you tried using the Shared Folder in the Devices menu?

---

### Post by abhilashm86 on 2011-01-31
> **metalf8801 said:**
> Have you tried using the Shared Folder in the Devices menu?

I tried it a long back, when i do shared folders, ubuntu will auto mount drives in /media/drives. So i can't even copy, create folders there since /media/drives belong to user root!! 

I even tried changing owner, file permissions to /media, but its taking since drives from windows are ntfs!!

---

