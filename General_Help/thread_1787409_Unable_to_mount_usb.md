---
title: "Unable to mount usb"
date: 2011-06-21
forum: General Help
---

### Post by SleepCat on 2011-06-21
I wanted to mount iso files on ubuntu 10.04, and tried this nautilus script. ([http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html))

It didn't work, and now I can't mount ubs-sticks! When I try to, I just get a pop up window, telling me it failed to do so.

How do I undo this? :(

---

### Post by nomko on 2011-06-21
Iso files are easy to mount with a simple command:
```
sudo mount {filename}.iso cdrom -o loop
```. This should do the trick.
 
There are also programs (most of them can be found in the repositories):
- AcetoneISO
- Gmount-Iso
- Fuseiso
 
 
There's also a help page available: [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso).
 
About your problem of not mounting USB i'm not really helpfuill, i know.
Maybe you can find a solution here:
[http://ubuntuforums.org/showthread.php?t=1786458&highlight=mounting+usb](http://ubuntuforums.org/showthread.php?t=1786458&highlight=mounting+usb)
[http://ubuntuforums.org/showthread.php?t=1518031&highlight=mounting+usb](http://ubuntuforums.org/showthread.php?t=1518031&highlight=mounting+usb)
[http://ubuntuforums.org/showthread.php?t=1618085&highlight=mounting+usb](http://ubuntuforums.org/showthread.php?t=1618085&highlight=mounting+usb)
[http://ubuntuforums.org/showthread.php?t=1785535&highlight=mounting+usb](http://ubuntuforums.org/showthread.php?t=1785535&highlight=mounting+usb)
[http://ubuntuforums.org/showthread.php?t=1518031&highlight=mounting+usb](http://ubuntuforums.org/showthread.php?t=1518031&highlight=mounting+usb)

---

### Post by SleepCat on 2011-06-21
Thanks for the tip! :)

But I just want to know how I can delete those two scripts again, since I didn't have problems mounting usb's before I installed the scripts.

---

### Post by nothingspecial on 2011-06-21
```
rm ~/.gnome2/nautilus-scripts/mount.sh ~/.gnome2/nautilus-scripts/unmount.sh && nautilus -q
```

---

