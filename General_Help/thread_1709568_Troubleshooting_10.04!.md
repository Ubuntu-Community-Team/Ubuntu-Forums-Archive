---
title: "Troubleshooting 10.04!"
date: 2011-03-18
forum: General Help
---

### Post by Advice Pro on 2011-03-18
I upgraded to 10.04 via, the Update manager, attempting to solve the usb issue in [Troubleshooting 9.10!](http://ubuntuforums.org/showthread.php?t=1704526), but got these errors:

```
Grub failed to install to the following devices:
/dev/sdd
```
```
Unknown media type in type 'all/all'
Unknown media type in type 'all/all files'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
```

Yet the issue remains of not being able to open my usb devices via *Computer*.

I've attached a ```
dmesg > dump.txt.zip

```

---

### Post by Advice Pro on 2011-03-23
The dump file in attached to my first post contains this line:
```
[    7.376548] sd 7:0:0:2: [sde] Write Protect is on
```
How do you turn off write protection?  I opened the /media directory via:
```
gnome-open /media
```
The attached screen shots are of /media and the message I got after opening the top left icon. The top right icon is my SD card:

---

