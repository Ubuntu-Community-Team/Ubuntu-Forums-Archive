---
title: "Uninstall latest kernel?"
date: 2011-11-11
forum: General Help
---

### Post by Carbs70 on 2011-11-11
Hi all,

Is there anyway to "uninstall" the latest kernel from grub?

I've got an issue with not being able to login to console [http://ubuntuforums.org/showthread.php?t=1879110](http://ubuntuforums.org/showthread.php?t=1879110) and in the absence of any help/solutions there, it would be really useful for me to uninstall the latest kernel so that grub is booting into the last working pairing of kernel and graphics driver.....

---

### Post by blueridgedog on 2011-11-11
You should be able to uninstall it via synaptic.

---

### Post by Enigmapond on 2011-11-11
I wouldn't uninstall it, if you install Startup Manager you can change the default to login to the previous kernel. If you really want to uninstall it yes...you can do it in synaptic but if you have Ubuntu Tweak, boot into the previous kernel and access the  package cleaner in tweak and there is a section to purge the kernel which will delete the kernel, image and configuration...

---

### Post by Carbs70 on 2011-11-12
Cheers for that - Startup Manager was exactly the solution I was after. At least the default kernel now has a working Nvidia Driver. :)

Now I can get back to trying to work out WTF is going wrong when trying to login to console...

---

