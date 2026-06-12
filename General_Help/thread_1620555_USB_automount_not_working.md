---
title: "USB automount not working"
date: 2010-11-13
forum: General Help
---

### Post by maxi961 on 2010-11-13
HP dv6020 laptop - ubuntu 10,10 x86

Very strange situation: today when I inserted my usbpen in the laptop, automount did not work. I tried another pen with same result. I checked with mountmanager and both pens were working and actually mounted them manually, but automount which worked perfectly yesterday now is dead.
I found a workaround installing usbmount from standard repository and now automount works again but usbpens are mounted in /MEDIA/usbx instead with their names as before and I have to open a root terminal tu unmount.
Unfortunately I use a pen for backup with unison and changing the mount position I have to modify unison profile every time, which is pretty uncomfortable.
The problem May arise from the fact thgat yesterday I tried to manually compile and install the canon driver for my printer and trying to solve dependencies I had to compile and install Glib-2.26 pango-1.28.3 and gtk+2.22 from their sources.
I did not manage to get a working canon driver but i may have made a mess with usb automount function.
Can anyone please tell me which program/service is responsible for usb automount in ubuntu 10.10 so that i can reinstall or reconfigure it.
Thanks

Max

---

### Post by lmarmisa on 2010-11-13
Maybe the directory used by automount was not deleted and this is the cause of the problem.

Open a terminal and type this command:

> 
ls -l /media


Check if the folder for the automount of the pendrive is there when the pendrive is not connected (post the output of the command if you wish).

---

### Post by maxi961 on 2010-11-13
Already checked, neither name form my usbpen are left in /media directory.
The usbx directories have been created after installing usbmount.

ls -l /media output

> totale 44
drwxr-x--- 2 root root 4096 2010-10-14 20:48 apt
lrwxrwxrwx 1 root root    6 2010-06-28 09:03 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-06-28 09:03 cdrom0
drwxr-xrwx 2 root root 4096 2010-10-29 20:24 iso
lrwxrwxrwx 1 root root    4 2010-11-13 09:04 usb -> usb0
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb0
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb1
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb2
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb3
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb4
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb5
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb6
drwxr-xr-x 2 root root 4096 2010-11-13 09:04 usb7

---

### Post by lmarmisa on 2010-11-13
Why do you have so many usbx directories?.

Have you created them?.

---

### Post by maxi961 on 2010-11-13
Really don't know: those directories have been created after installing usbmount and are used by that program for mounting usb devices, previously directories were created when needed and deleted after use, but I do not know which program/service was in charge of the mounting operation.

Max

---

### Post by lmarmisa on 2010-11-13
I believe that these /media/usbx directories are the origin of your problem. You should delete them.

```

sudo rm -r /media/usb* 			 		

```

Please, read this thread describing your same problem and its solution:

[http://ubuntuforums.org/showthread.php?p=9376116](http://ubuntuforums.org/showthread.php?p=9376116)

---

### Post by maxi961 on 2010-11-15
Sorry, but that is not the solution: those usbx directories where created installing (and configuring) the program usbmount. those dirs where not present before installing that program ann the problem was already there. After installing usbmont the usb peripherals are automounted, but with usbx names insteade od name of usbpen as it was before.
Anyway now I will solve the proble in another way: I have't been able to compile a working driver for my canon 4380 multifuntion so I will delet ubuntu 10.10 installation and revert to 10.04 where the binaries provided by canon are working.
Thank for your cooperation.

Max

---

### Post by ktmom on 2010-12-24
Thanks lmarmisa.

Those directories were created today when I installed usbmount and removing them was the way to get the hot mount to work for my myth install.

---

