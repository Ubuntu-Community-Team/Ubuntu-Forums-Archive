---
title: "argh - cdrom will now eject"
date: 2006-06-14
forum: General Help
---

### Post by c-m on 2006-06-14
I need to eject my cd in order to complete the installation of a game and insert disc 2, but the drive will not eject

carl@carl:~/TransGaming_Drive$ umount /dev/cdrom && eject
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
carl@carl:~/TransGaming_Drive$

carl@carl:~/TransGaming_Drive$ sudo umount /media/cdrom0
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
carl@carl:~/TransGaming_Drive$ eject
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed

---

### Post by Sir_Yaro on 2006-06-14
First close any window, console etc which is opened on cdrom directory. Or just change directory....

---

### Post by c-m on 2006-06-14
I don't have any directories open using the cdrom, the only thing using it is cedega since i'm trying to install a game and need to insert disct 2.

I cant just turn the computer off since then i'll lose half the install.

I don't see why the damn thing just wont eject, its all abit silly

---

### Post by firetux on 2006-06-14
My search on google(I don't use cedega) told me you should use the "-monitor-cdrom-eject"-option when starting cedega. 

t appears to be a very common problem, so I think its really weird you did't find any solution looking for it on google.

---

### Post by PriceChild on 2006-06-14
I'm having problems with cedega c-m :(
 
It won't recognise my cd drives and therefore it won't start games past hte copy protection!!! :(
 
Pressing mount just tells me it hasn't got any media.
 
Have you had this problem on Dapper? Please help, Pricey

---

### Post by c-m on 2006-06-15
[QUOTE=PriceChild]I'm having problems with cedega c-m :(
 
It won't recognise my cd drives and therefore it won't start games past hte copy protection!!! :(
 
Pressing mount just tells me it hasn't got any media.
 
Have you had this problem on Dapper? Please help, Pricey[/QUOTE]
Sorry mate, I haven't had any problems like that. What i'd suggest if you can get it working is just to create an ISO of the media then mount it and install from there. 

I never run my games from within the programme, i run it from the command line, cedega generals.exe, hopefully it'll be able to recognise the Cd drive that way. If not a nocd patch might be your only option.

---

### Post by tiftmasta on 2006-06-24
I don't know about using cedega but using wine I believe you can do the following:

use winecfg and make sure that the setting for your cd-rom drive is actually set on that and not hard disk.

While wine is running you can use:
wine eject

I think that'll work...

---

### Post by PriceChild on 2006-06-25
wine won't handle most games like BF2 for example... and definately doen't do the copy protection, or as good 3d rendering.

---

