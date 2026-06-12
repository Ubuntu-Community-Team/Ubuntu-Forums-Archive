---
title: "USB Stick is mounted read-only"
date: 2012-02-29
forum: General Help
---

### Post by silviutp on 2012-02-29
I don't know when this happened but whenever I want to use a USB stick with a ntfs partition it is mounted read-only.
I have also tried to mount it manually and will not allow me to mount it with write access.
The same problem was with a ntfs partition...
The partition on the usb stick is also ntfs. This does not happen on a fat32 partition.
Anybody has a clue about this ?

I'm using Ubuntu 11.10 on x86_64 system.

Thank you.

---

### Post by raja.genupula on 2012-02-29
[FONT=Verdana][SIZE=2]Yeah got something 
[http://ubuntuforums.org/showthread.php?t=899060&page=2](http://ubuntuforums.org/showthread.php?t=899060&page=2)

If that wont help then look for this "[/SIZE][/FONT][FONT=Verdana][SIZE=1][SIZE=2]Device become suddenly read only" in the link
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

observe   the output of **dmesg** after you plugin your device . 

All the best . [/SIZE]
[/SIZE][/FONT]

---

### Post by silviutp on 2012-02-29
*If you see "Write Protect is off" and no errors in your logfiles, than you should set filesystem type specific mount options (FS_MOUNTOPTIONS) in /etc/usbmount/usbmount.conf. Wrong gid causes mounting read only.*

I can see this message in the **dmesg** output after I plug in the usb stick, but there is no /etc/usbmount for my distribution. Do you know how did this change for Ubuntu 11.10 ?

---

### Post by raja.genupula on 2012-02-29
actually that have to be install
```
sudo apt-get install usbmount
```

---

