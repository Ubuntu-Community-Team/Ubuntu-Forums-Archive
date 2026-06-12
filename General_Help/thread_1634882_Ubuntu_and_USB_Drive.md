---
title: "Ubuntu and USB Drive"
date: 2010-12-01
forum: General Help
---

### Post by rumpus on 2010-12-01
Hi All. Im pretty new to ubuntu and just trying to learn my way around it..

My main issue at the moment i cant figure out is how to get a USB stick to work without having to stuff around..

Currently I plug in the USB Stick and in my places menu get usb0 and 4gbUSB. I can read the 4gbUSB but cannot write unless i open terminal and $sudo umount usb0

This is ok for me but my missus is a old windows user and its a bit past her.. Is there a way to get write access to the stick without needing the terminal?

thanks

---

### Post by surfer on 2010-12-01
what filesystem is on the stick? if it is formatted win fat32, there should be no problem writing to it. it will mess up file permissions when you write on it though. but that is usually not that bad.

you find out about the filesystem in System -> Administration -> Disk Utility or with
```

$ cat /etc/mtab

```

---

### Post by rumpus on 2010-12-01
It is FAT32,

I can open it as usb0 but only read.....

But as 4gbUSB it does not open at all...

probably something stupid im missing...

---

### Post by killa.fr0gg on 2010-12-01
Who formatted it? Back it up and reformat it. One of those obvious things, maybe...

---

