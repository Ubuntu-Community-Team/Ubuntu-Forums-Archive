---
title: "Black screen after boot"
date: 2011-01-27
forum: General Help
---

### Post by byte1918 on 2011-01-27
Hello,

Ubuntu was working fine last night and as far as I remember I haven't installed anything new or change any system files but today when I booted up I got a black screen, and also the keyboard doesn't seem to work, not sure about the mouse (I can't see the cursor). I went in Recovery Mode I used the "Repair broken packages" and I think it downloaded a new version of the kernel, but the black screen was appearing before too so this isn't the cause. I also tried the graphical failsafe mode and I have selected to use the generic drivers. At the next restart the screen was still black, but this time I could hear the ubuntu boot up sound. I'm not really sure what is causing this but I think it has something to do with the video card drivers. I have an ATI card and I use the proprietary drivers.

If anyone can help, I would very much appreciate it.

Thanks

---

### Post by pl@yer on 2011-01-27
Possibly an update has overwritten some files used by the proprietary driver. 
Try reinstalling the proprietary drivers from terminal ctrl+alt+f2.

---

### Post by marin123 on 2011-01-27
[http://ubuntuforums.org/showthread.php?t=1663916](http://ubuntuforums.org/showthread.php?t=1663916)

same thing here. its xorg updates that do that. avoid updating xorg in the future.

---

### Post by byte1918 on 2011-01-27
> **pl@yer said:**
> Possibly an update has overwritten some files used by the proprietary driver. 
Try reinstalling the proprietary drivers from terminal ctrl+alt+f2.

The thing is that this happened before the update. I will try to reinstall the driver and see what happens.

---

### Post by marin123 on 2011-01-27
make sure you reinstall drivers from the source you already had. example: i installed drivers from ati website and after that i had to reinstall that same driver (i couldnt reinstall xorg-server and xorg-common).

---

### Post by byte1918 on 2011-01-27
> **marin123 said:**
> make sure you reinstall drivers from the source you already had. example: i installed drivers from ati website and after that i had to reinstall that same driver (i couldnt reinstall xorg-server and xorg-common).

Yeah, you were right, I reinstalled the drivers from ATI website, and it's working now. Thanks a lot for the help.

---

### Post by pl@yer on 2011-02-02
> **marin123 said:**
> make sure you reinstall drivers from the source you already had. example: i installed drivers from ati website and after that i had to reinstall that same driver (i couldn't reinstall xorg-server and xorg-common).

Usually the binary driver will have an uninstall option. After running the binary driver's uninstall, you should be able to install the version provided by your distro. Try running --help on the binary. If it was compiled by hand you can usually run "make uninstall" in the same dir that you ran "make install".

for nvidia Running
```

NVIDIA-Linux-x86-260.19.21.run -A

```
will show that there is a --uninstall switch to unintall the driver.

---

