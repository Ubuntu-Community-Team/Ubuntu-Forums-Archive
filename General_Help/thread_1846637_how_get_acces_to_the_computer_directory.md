---
title: "how get acces to the computer directory"
date: 2011-09-19
forum: General Help
---

### Post by unknow04 on 2011-09-19
the computer directory is where all devices connected are isn't ? so how can i go there whit the terminal ?

---

### Post by Frogs Hair on 2011-09-19
See File & Directory Commands .[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by unknow04 on 2011-09-19
Man I already did but it doesn't say anything about that, so question is how can i acces to an usb directory from terminal ?

---

### Post by haqking on 2011-09-19
> **unknow04 said:**
> Man I already did but it doesn't say anything about that, so question is how can i acces to an usb directory from terminal ?


usually mounted in /media

so you can use absolute or relative paths:

```
cd /media
```

---

### Post by 3rdalbum on 2011-09-19
> **unknow04 said:**
> the computer directory is where all devices connected are isn't ? so how can i go there whit the terminal ?

That directory doesn't really exist. It's just a "virtual" directory that exists only in Gnome's imagination.

Most mounted disks are mounted in /media, typically. If you're looking for a mounted disk, look there.

Network drives such as SMB, FTP, and SSH are typically mounted in ~/.gvfs - that's a hidden directory called ".gvfs" that's inside your home directory.

---

### Post by unknow04 on 2011-09-19
thanks a lot for your answers, actually is not a usb is a external hard disk

---

### Post by haqking on 2011-09-19
> **unknow04 said:**
> thanks a lot for your answers, actually is not a usb is a external hard disk


which probably connects via USB so again as i said before:

```
cd /media
```

a device can be anything, if it connects via USB then it is USB regardless of what it it used for.

---

### Post by Neill_R on 2011-09-19
> **unknow04 said:**
> Man I already did but it doesn't say anything about that, so question is how can i acces to an usb directory from terminal ?
 
I would type the command 
 
sudo lsusb 
 
in a terminal window

---

