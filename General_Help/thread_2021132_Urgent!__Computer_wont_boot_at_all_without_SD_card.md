---
title: "Urgent!  Computer wont boot at all without SD card inserted!"
date: 2012-07-08
forum: General Help
---

### Post by Divisi on 2012-07-08
Ok as it says in the title, my computer wont boot at all without the sd card in.  Not even to the Windows XP i have installed.  

When I remove the sd card i get this:
```

error: unknown filesystem.
grub rescue>

```It will allow me to press enter and type, but I have no idea what to do about this, and once I put the SD card back in it works just fine. 
This must have happened just after I installed Xubuntu because I haven't had this problem before.

I would appreciate any help I can get because i don't want to rely on having an SD card in to keep my computer working.

Thanks ):P

edit: The SD card could be the problem of this, but Xubuntu seems to boot very slowly, I'm not sure if this helps anything, but if this problem is fixable I would like to get some help on making it boot faster, thanks again.

---

### Post by efflandt on 2012-07-08
You apparently accidentally installed grub to your SD card instead of the MBR of your main hard drive.  You can typically fix that by booting into Ubuntu on your hard drive, assuming that sda is your boot drive, and doing:

```
sudo grub-install /dev/sda
```

---

### Post by Divisi on 2012-07-08
All I got was 

Installation finished.  No error reported.

Is it just gonna work now?

---

### Post by Divisi on 2012-07-08
It worked!  For some reason it didn't work the first time, but I tried again and it worked.

Thanks!!

---

