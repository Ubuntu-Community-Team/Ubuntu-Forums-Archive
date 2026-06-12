---
title: "Error In mounting drive and error in /media"
date: 2010-08-07
forum: General Help
---

### Post by ak4allz on 2010-08-07
Hi there, i hope that anyone can solve these problems.
First, when i inserted my pendrive, i got this message, and the nautilus opened for me 2 windows for my pendrive, simultaneously.
[IMG]http://img821.imageshack.us/img821/920/errormountingdrive.png[/IMG]

And, when i go to the /media, i got this.
[IMG]http://img193.imageshack.us/img193/3664/crazyslashmedia.png[/IMG]

I don't know what had happen. If someone can help me figure out how to solve that, thanks a lot.

---

### Post by sideaway on 2010-08-07
replace ext3, sdf1 and usb-backup with your pendrives details...


1. Launch 'gconf-editor' and browse to 'apps / nautilus / preferences'
- uncheck 'media_automount'
- uncheck 'media_automount_open'

2. Launched GParted to find the id of the location of the device (/dev/sdf1)

3. run

```
sudo mount -t ext3 -o rw,users /dev/sdf1 /media/usb-backup
```

This will take a while...

unmount with
```

sudo umount /media/usb-backup
```

and removed the device

Then re-enable the Nautilus preferences unset in step 1.

Plug in the device again.

---

### Post by ak4allz on 2010-08-08
well, for solving the problem "error mounting device", it is a clear instruction for me but for the second one, it is unclear instruction. Can you please give me the explanation of the syntax? thanx

---

