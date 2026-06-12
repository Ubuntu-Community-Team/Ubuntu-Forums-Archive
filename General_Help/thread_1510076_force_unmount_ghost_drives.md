---
title: "force unmount ghost drives?"
date: 2010-06-15
forum: General Help
---

### Post by abumaia on 2010-06-15
I think something might be wrong with one of my usb ports on my laptop.  If I move my laptop the wrong way, my external hard drive gets momentarily disconnected/reconnected, and each time this happens, it gets mounted to a new location.  The hard drive is labeled as Media, and at the end of the day, in the /media directory I usually end up with Media, Media_, Media__, Media___, Media____, etc.  None of these "ghost drives" can be unmounted.  I get an error saying that the drive is not in fstab, and I'm not using sudo.  So I open nautilus with sudo, and still cannot unmount these drives.

What can I do (short of rebooting) to get rid of the ghost drives?

---

### Post by JustinR on 2010-06-15
Go into a terminal and try it that way.

```
sudo umount /media/Media_
```

and so on for the other mount folders.

---

### Post by abumaia on 2010-06-15
I had tried that method, but it just hung in terminal.  I ended up doing a reboot, so next time it happens I'll try it again and will be a little more patient with it.

---

### Post by jerome1232 on 2010-06-15
It's probably not actually mounted to those spots, and you can safely delete them as they are just folders that didn't get removed automatically.


First check though, after this has happened a few times what's the output of the following command? So long as your external isn't actually mounted to any but the latest spot (which I suspect is true) you can just remove the older folders using sudo rmdir. note rmdir is fairly safe to use as it will ONLY remove empty folders.
```
mount
```

---

### Post by delcypher on 2010-06-15
You can see what applications are using a particular mount point by running

```
sudo fuser -m /media/Media_
```

You can try to kill those processes to, but use at your own risk

```
sudo fuser -ik -m -/media/Media_
```

---

