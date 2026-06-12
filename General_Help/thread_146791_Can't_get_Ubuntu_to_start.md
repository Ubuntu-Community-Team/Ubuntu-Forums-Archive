---
title: "Can't get Ubuntu to start"
date: 2006-03-19
forum: General Help
---

### Post by wile_e8 on 2006-03-19
I was having wireless issues, and while I was messing with it I rebooted.  When Ubuntu was loading up the wireless, I got this error message:

```
[XXXXXX.XXXXXX] ipw2200: Firmware error detected.  Restarting
[XXXXXX.XXXXXX] ipw2200: Sysfs 'error' log already exists.
```

And it keeps printing this message over and over on the screen with the XXXXXX.XXXXXX being a number that increments.  And it never stops.  So I'd want to reinstall the firmware and drivers for my wireless to fix it, except this never stops and Ubuntu never loads.  Is there any way to get this to stop so I can make the changes?  Tell it that I don't want it to keep restarting, just give up don't load the wireless?

---

### Post by Trab on 2006-03-19
boot in safe mode in grub.
that will get you to a root prompt
from there you can tweak stuff
alternatively u could use a liveCD and mount your hdds there...
good luck!

---

### Post by wile_e8 on 2006-03-19
How do I boot into safe mode?  Is that recovery mode?  Because that has the same problem.

And what is the LiveCD?  Can I do that with my CD I used to install Ubuntu, or do I need to make another CD?

Sorry for the simple questions, I'm pretty new to linux.

---

### Post by taurus on 2006-03-19
LiveCD is not the same as the install CD.  With LiveCD, you boot and run Ubuntu entirely from the CD--LiveCD--so if you have problem with your Ubuntu on your machine, you can use the LiveCD to fix it.  So if you don't have it, you need to download it and burn it to a CD.

---

### Post by wile_e8 on 2006-03-19
I've booted the LiveCD, and I mounted the installed Ubuntu file directory in the /mnt folder.  Thanks for the help and direction on that.  But now I would like to know what I need to do to remove the errors.  I installed wifi + wpa as described in [post=130227]this[/post] post.  Normally if my wifi was acting up, I would just run through the steps again, but this I don't know if it would work with the new directory structure.  Does anyone know if these steps would still work with the directory stucture in LiveCD?  Or it would be just fine if someone knew what folders/files to remove to get rid of the drivers, that would hopefully get rid of the errors and let the installed version Ubuntu load and I could do the rest from there.

---

