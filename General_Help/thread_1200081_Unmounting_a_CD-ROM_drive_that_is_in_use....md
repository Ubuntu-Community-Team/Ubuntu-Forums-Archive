---
title: "Unmounting a CD-ROM drive that is in use..."
date: 2009-06-29
forum: General Help
---

### Post by CinderWild on 2009-06-29
Here is the problem. I am attempting to install a multi-disc game through Wine. I got through the installation of the first disc, but when it asks me to insert the second disc I can't open my CD drive. An error pops up that says the drive cannot be unmounted because it is being used by another application. I tried "sudo umount -f cdrom0" but I got a similar error in the terminal. Is there any way to do this? Thanks in advance.

---

### Post by ajgreeny on 2009-06-29
May not help but the command should be ```
sudo umount -f /media/cdrom0
```

---

### Post by CinderWild on 2009-06-29
Oh sorry. I miss-typed my post. Yeah I did that command and got the same error as pressing the eject button did. Something along the lines of "Unable to unmount volume because another process is using it." I even tried right clicking it and clicking "Unmount." I guess since Wine is using the volume it won't unmount, but I can't continue the installation if I can't put in the next CD!#-oThere has to be a way to do this though...

---

