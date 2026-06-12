---
title: "mount hard drive"
date: 2010-06-30
forum: General Help
---

### Post by alenn on 2010-06-30
how to keep mounted my hard drive even when I restart my computer, I mean, how to set my ubuntu to automount my second hard drive every time I turn on my compputer.  

I hope you understand me.

---

### Post by mikewhatever on 2010-06-30
What kind of drive, internal or external? Usually, a line in fstab does the trick.

---

### Post by VCoolio on 2010-06-30
Put a line in /etc/fstab, howto [here](http://ubuntuforums.org/showthread.php?t=283131&highlight=howto+fstab). Like this:
```
/dev/<drive> /media/<mountfolder> ntfs-3g defaults 0 0
```

Find <drive> with 'sudo fdisk -l', make sure the mountfolder you choose exists. Change ntfs-3g to whatever filesystem the drive has. Modify options as you wish.

---

### Post by alenn on 2010-06-30
internal HDD

---

### Post by dino99 on 2010-06-30
mountmanager (synaptic) take care of your partitions and devices as you need

---

### Post by alenn on 2010-06-30
alright I've fixed it eith Storage Device Manager, now how to remove those icons of my mounted drives, I just want to keep USB icon but want to remove HDD icons from desktop.

---

### Post by VCoolio on 2010-06-30
Maybe it's in nautilus > edit > preferences (your file manager which is also responsible for your desktop icons); else open gconf-editor and browse to apps > nautilus > desktop and see what you can do there.

---

### Post by alenn on 2010-06-30
can't find nautilus, where is it?

---

### Post by Morbius1 on 2010-06-30
Anything mounted to /media or your /home/username directory will show up on the desktop.

Anything mounted to /mnt or to / directly ( for example, /Windows ) will not show up on the desktop.

Nautilus is the file manager.

---

