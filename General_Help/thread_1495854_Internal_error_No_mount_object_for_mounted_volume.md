---
title: "Internal error: No mount object for mounted volume"
date: 2010-05-28
forum: General Help
---

### Post by hihihi100 on 2010-05-28
Internal error: No mount object for mounted volume

Thats what happens when I try to mount an external hard drive, it has happened since the upgrade to 10.04 lucid.

tips please

---

### Post by lmarmisa on 2010-05-28
Maybe GParted could help you. Install it using Synaptic.

---

### Post by lmarmisa on 2010-05-28
Sometimes there are some problems and Ubuntu does not delete the mount directories.

Type this command with your external drive unplugged:

> 
ls -l /media


---

### Post by hihihi100 on 2010-05-28
total 36
lrwxrwxrwx 1 root root    6 2010-04-16 16:53 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-04-16 16:53 cdrom0
lrwxrwxrwx 1 root root    4 2010-05-10 15:38 usb -> usb0
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb0
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb1
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb2
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb3
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb4
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb5
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb6
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb7

---

### Post by lmarmisa on 2010-05-28
Your list seems cut off. Anyway, these usbx directories look suspicious. They were created on May 10th, 3 weeks ago.

Could you post the complete output of these commands?

> 
ls -l /media
ls -l /media/usb2


---

### Post by hihihi100 on 2010-05-28
almost the same:

ls -l /media
total 36
lrwxrwxrwx 1 root root    6 2010-04-16 16:53 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-04-16 16:53 cdrom0
lrwxrwxrwx 1 root root    4 2010-05-10 15:38 usb -> usb0
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb0
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb1
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb2
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb3
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb4
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb5
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb6
drwxr-xr-x 2 root root 4096 2010-05-10 15:38 usb7
hihihi100@hihihi100-laptop:~$ ls -l /media/usb2 
total 0
hihihi100@hihihi100-laptop:~$

look suspicious?? why? could it be that I need to uninstall some USB related packages from synaptic?

cheers

---

### Post by lmarmisa on 2010-05-28
Try this command (external drive disconnected, please):

> 
sudo rm -r /media/usb*


If these directories are deleted, maybe you will be able to mount again your external hard drive.

Reboot your system and check if the problem is solved.

---

### Post by hihihi100 on 2010-05-28
k, proceeding to reboot...

---

### Post by hihihi100 on 2010-05-28
haha, that worked perfectly man, thx...

Now the external hard drive mounts automatically when plugged in. great, Its the first time it happens since the upgrade..

thread solved

thx

---

