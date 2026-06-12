---
title: "I delete Ubuntu partition then i can not use my computer"
date: 2011-11-27
forum: General Help
---

### Post by iamkanoot on 2011-11-27
my computer booted dual OS windows 7 and Ubuntu.i deleted the Ubuntu partition then i can not use windows 7.i try to use Unbutu Live CD to fix mbr problem.what i have done many suggestion on the Internet but still doesn't work for me.

Here is the method i did
-------------------------------------------------
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

result:

Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
----------------------------------------------------

then reboot and i see this
[IMG]https://lh3.googleusercontent.com/-o8g6iKGoXzs/TtIA38v5YxI/AAAAAAAASRw/KX3NSKH13Sc/s640/photo.JPG[/IMG]

thank you very much

---

### Post by decrepit on 2011-11-27
well you've managed to hand the boot up back to windows, so the problem is no longer ubuntu's but something wrong with windows.
Have you got the windows disk?

---

### Post by elliotn on 2011-11-27
put in your Windows 7 disk and do a boot repair and rewrite your mbr

---

### Post by digithal on 2011-11-27
Boot using Windows 7 setup DVD and click on "Repair Computer". Then click on "Command Prompt". Now navigate to your DVD drive using "CD" command and at last provide following command:
```
bootsect /nt60 c: /mbr
```

---

### Post by iamkanoot on 2011-11-27
thank you very muck Can i fix this problem without using disk.because i dont have any with me.

---

### Post by iamkanoot on 2011-11-28
Thank you very much for all of your answers verything is all set now

---

