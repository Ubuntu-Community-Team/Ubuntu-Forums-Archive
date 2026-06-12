---
title: "Reinstalling kernel from installer CD"
date: 2010-09-15
forum: General Help
---

### Post by EricTyrrell on 2010-09-15
I'm using Ubuntu 10.04 Server x64 and tried to update the kernel to a virtual kernel. The kernel install failed and when I rebooted grub couldn't find any kernel to load. How do I reinstall the kernel from the installer cd?

Thanks

---

### Post by harrismh777 on 2010-09-15
You could try to update from from the CD. 

Sometimes, depending on how badly you shot your foot, its just better to get a new foot.

You could boot-up the CD, mount your hard-drive, back-up what-ever data, and reload the system. 


:idea:

---

### Post by EricTyrrell on 2010-09-15
That's a last resort option. I really need to figure out how to reinstall the stock kernel from the cd.

---

### Post by TwelveGauge on 2010-09-15
> **EricTyrrell said:**
> That's a last resort option. I really need to figure out how to reinstall the stock kernel from the cd.

It's honestly easier to simply grab your files and reinstall.

---

### Post by EricTyrrell on 2010-09-15
Is it not possible to use the cd's rescue mode, mount the file system, and just apt-get my old kernel? When I tried this it seemed to work, but when I restarted it complained the file system was damaged and couldn't fix it.

---

### Post by CharlesA on 2010-09-15
> **EricTyrrell said:**
> Is it not possible to use the cd's rescue mode, mount the file system, and just apt-get my old kernel? When I tried this it seemed to work, but when I restarted it complained the file system was damaged and couldn't fix it.

EDIT: Better idea is this: Boot off the Ubuntu Server install disk and select "rescue a system" and follow the prompts and select /dev/sda1 or whatever yer root partition is and drop to a root shell.

Run this:

```
apt-get install linux-image-2.6.32-24-server
```

Then type *exit* and reboot the system.

---

### Post by EricTyrrell on 2010-09-15
I had actually tried a variation of that before, but now it works. I had to run fsck for some reason though. Thanks for your help.

---

