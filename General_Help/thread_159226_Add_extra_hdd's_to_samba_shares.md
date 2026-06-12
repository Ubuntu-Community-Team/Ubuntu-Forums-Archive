---
title: "Add extra hdd's to samba shares"
date: 2006-04-12
forum: General Help
---

### Post by leftyman on 2006-04-12
Hello:

I have succesfully installed samba to share files between my ubuntu and my windows xp pro laptop.

In my ubuntu computer I have 2 Hdd's only for storage (sda1 for example). I want to add them to my samba shares but I dont know how to do it.

thanks

---

### Post by Ramses de Norre on 2006-04-12
Easy way: system > administration > shared folders

Hard way: sudo gedit /etc/samba/smb.conf
The very last lines of the file define the shared folders.

---

### Post by leftyman on 2006-04-12
Thank you



I am a suuuuuuuuupernewbie as you can see


thanks again

---

