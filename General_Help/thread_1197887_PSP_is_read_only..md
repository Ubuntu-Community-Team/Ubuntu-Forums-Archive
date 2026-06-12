---
title: "PSP is read only."
date: 2009-06-26
forum: General Help
---

### Post by shanee753 on 2009-06-26
I have been trying to add a new video to my PSP for the last few hours. When I plug my PSP into my laptop using the usb wire it appears on my desktop then if I try to drag my video onto my PSP it wont let me because my psp is read only.
Sorry I'm very new to Linux and really can't work out what to do. I have tried opening my PSP as root and right clicking and trying to change permissions. Any help would be much appreciated!

---

### Post by thebigbluecan on 2009-06-26
Try going to terminal and type " gksudo nautilus " and type in your password when prompted.. Go to your PSP folder /media/PSP  and right click it and go to Properties then Permissions and change the permissions to your name and allow read and write. Let us know if you get it working :)

---

### Post by shanee753 on 2009-06-27
> **thebigbluecan said:**
> Try going to terminal and type " gksudo nautilus " and type in your password when prompted.. Go to your PSP folder /media/PSP  and right click it and go to Properties then Permissions and change the permissions to your name and allow read and write. Let us know if you get it working :)

Thanks for replying whenever I try to access it now I get a message saying "Invalid mount option when attempting to mount the volume." I think I've changed some of the options at some time when I was trying to get it so work. Sorry about that :/ any ideas how to change the mount options so I can try what you said?

edit:I think at one point I right clicked it on the desktop then property then changed some of the mount options. However as it is no longer mounting I cant right click it to change the options back :/

edit: also I'm using jaunty jackalope Ubuntu and my PSP appears in /media/disk

---

### Post by shanee753 on 2009-06-29
Bump, anyone know how I can fix this?

---

### Post by itsjareds on 2009-06-29
So is /media/disk the mounted PSP?

If not, try:
```
cd /media
sudo mkdir psp
sudo mount disk psp
```

---

### Post by Anxious Nut on 2009-06-29
This happens to me when I unplug my PSP without unmounting, and it becomes read-only. What I do next is not the best sulotion but it always works with me!


-Copy all folders(memory stick files) onto Desktop, Make sure all files are there
-Unplug your psp and goto (in psp) settings --> System settings --> Format Memory Stick

Yes formating, it's the only way I know (although i know it's not the right way, but it works)

-after formating plug it and copy all your files(you've copied earlier onto your computer)
-Paste them onto your PSP memory stick

**-UNMOUNT IT AND WAIT TILL a popup shows "safe to remove"**

enjoy

---

### Post by shanee753 on 2009-07-01
Thanks, I will try formating after but at the moment I can't mount my psp to back up the data from it.
itsjareds this is what I got:
ellipsis@Play:~$ cd /media
ellipsis@Play:/media$ sudo mkdir psp
[sudo] password for ellipsis: 
ellipsis@Play:/media$ sudo mount disk psp
mount: special device disk does not exist

Thanks for your help so far, sorry for messing with my options before :/

---

### Post by Anxious Nut on 2009-07-01
Try to mount it on any other OS (like windows), if it worked, do the steps above, and I believe that once it's formatted It'll mount without any problems!

[It'd be much easier if passing your psp/memory stick over was possible;)]

---

### Post by shanee753 on 2009-07-04
Ok thanks. That should solve my problem then when I get round to doing it (booting into windows takes years!)

---

### Post by hyperdude111 on 2009-07-04
I hav had this problem with psp's, memory cards and all types of flash data storage. Formatting has so far been the only solution other than re-booting into another OS.

---

