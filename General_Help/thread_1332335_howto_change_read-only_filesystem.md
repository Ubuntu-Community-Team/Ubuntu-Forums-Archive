---
title: "howto change read-only filesystem?"
date: 2009-11-20
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2009-11-20
I have a usb flash drive that somehow has been changed to read-only and I can't delete from it or add to it. I've tried using chmod as root user, but guess I don't understand the way to do this since I am unable to get it to work for me. Is chmod the same as the MS-DOS attrib command? Or is there another command I should be using other than chmod?

Thanks

---

### Post by phillw on 2009-11-20
Hi ..

Pop it into the machine, Click on places & select it.
Click on media next to it in the window that opens.
Right Click On it and select properties, then the Tab Permissions.
You can set all the various permissions up from there - you can set it to allow everyone to write / read from it if it is just a general scratch disk.
Saves you wandering around chmod.

A good tutorial on chmod can be found here  [http://www.unixcities.com/howto/index3.html](http://www.unixcities.com/howto/index3.html)

It's worth a read to learn how linux handles various permissions and groups.

Regards,

Phill.

---

### Post by linux-hack on 2009-11-20
you can mount your USB like this :

mount -t (FILESYSTEM) -o rw,user,noexec /dev/USBDRIVE /mnt/MOUNTPOINT

---

### Post by ihatetryingtopickaloginna on 2009-11-20
> **phillw said:**
> Hi ..

Pop it into the machine, Click on places & select it.
Click on media next to it in the window that opens.
Right Click On it and select properties, then the Tab Permissions.
You can set all the various permissions up from there - you can 

All it has in 'Permissions' is The permissions of "disk" could not be determined.

---

### Post by phillw on 2009-11-20
> **ihatetryingtopickaloginna said:**
> All it has in 'Permissions' is The permissions of "disk" could not be determined.

Have you got any important data on it ?

If not, format it  [http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)

If you're going to use it near windows machines, you'll want the 
```
$ sudo mkfs.vfat /dev/sda1
```

Version - as it says -- make sure you get the device name correct - those commands WILL format what you tell them to - no 'Are you sure Y/N' stuff !!!

Phill.

---

### Post by ihatetryingtopickaloginna on 2009-11-20
Nothing I want to keep. Thanks for the help.

Al

---

