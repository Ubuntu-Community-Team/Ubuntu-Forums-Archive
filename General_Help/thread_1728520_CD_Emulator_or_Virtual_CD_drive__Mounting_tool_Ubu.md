---
title: "CD Emulator or Virtual CD drive?  Mounting tool?? Ubuntu"
date: 2011-04-13
forum: General Help
---

### Post by dumplingz on 2011-04-13
I recently downloaded torrent games. One of them is 7.2 GB disc file. (Iso). I don't have the disc which is 7.2GB in size. But the readme file says, you can mount the image????    I tried Gmount from Ubuntu software center and it had an error saying (An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so)

i have no clue.

---

### Post by bodhi.zazen on 2011-04-13
Could be a bad or corrupt download.

You do not need any program to mount ISO.

Open a terminal and try :

```
sudo mount -t iso9660 -o loop /full/path/to_your_.iso /mnt
```

Then 

```
ls /mnt
```

If you have a problem post the error message and the output of

```
dmesg | tail
```

---

### Post by linuxuser12345 on 2011-04-13
How about this: Don't illegally download games??

---

### Post by PCNetSpec on 2011-04-13
"Slight" modification to bodhi.zazen's solution

If you want it to appear on the desktop as a CD/DVD (with icon)

```
sudo mkdir /media/fakecd

sudo mount -t iso9660 -o loop /path/to/your.iso /media/fakecd
```

and unmount with

```
sudo umount /media/fakecd
```

Or you could just right-click the ISO and select **Open with>Archive Mounter**

---

### Post by dumplingz on 2011-04-13
well   sorry, im new to linux,,

i know the terminal thingo

how to i do it properly?  the cd file is called  (rld-scii.iso)  and i want to mount (final destination) desktop/My Property/Starcraft 2

soz, im learning :D

---

