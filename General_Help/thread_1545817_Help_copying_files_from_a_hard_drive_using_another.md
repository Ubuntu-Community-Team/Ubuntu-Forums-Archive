---
title: "Help copying files from a hard drive using another computer"
date: 2010-08-04
forum: General Help
---

### Post by Reshuken on 2010-08-04
Hello guys.
I got a problem with the motherboard of my computer and now I need to get some files out from the hard drive (an ext3 partition). I can access the files from another computer but because of the permissions of my user it doesn't let me copy the files over to another drive. Does anybody know a workaround for this problem? Any help is appreciated.
Just to give a little bit more info, my computer was running Kubuntu 8.10 with a Vista dualboot. I also tried attaching the hard drive to another laptop, but because of the video drivers the display doesn't function properly.

---

### Post by jimbop99 on 2010-08-04
Try booting to a live cd with both hard drives attached and see if you can transfer files.

---

### Post by -kg- on 2010-08-04
If you still have the hard drive connected to the other computer (and that computer is using Ubuntu), just launch Nautilus with root access by opening a terminal window and using the code:

```
gksu nautilus
```

The nautilus window that launches will have root access and you'll have full access to your files on the other hard drive.

Doing the operations from the Live CD will also work, as Nautilus will have root access by default.  If you would like a bit better speed (I do this as a matter of course, since it boots much quicker), you might want to make a Live CD installation on a USB Flash drive using Unetbootin (available in the repos, and a Windows version is also available).

---

### Post by Reshuken on 2010-08-04
Actually that's what I tried to do, but for some reason it won't allow me to copy the files. It gives me an error regarding permissions, which I assume are because the files are "owned" by me and not the live cd user.


***The answer above was meant for jimbop99, I will try what -kg- suggested.***

---

### Post by Reshuken on 2010-08-04
Thanks for all the help. I was able to get my files out of the hard drive.

---

