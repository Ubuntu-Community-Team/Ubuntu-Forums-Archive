---
title: "Dual Boot Windows XP and Ubuntu"
date: 2010-06-30
forum: General Help
---

### Post by Spirrwell on 2010-06-30
I currently have the latest Ubuntu OS on my computer. It's currently dual booting with Windows 7 which has been running badly. I know that if I install Windows XP I won't be able to boot into GRUB to boot Ubuntu. I need to work on a project that will probably only work on Windows. Is there a way to reinstall the GRUB boot loader after I install Windows XP? Sorry if this has already been asked, I could only find dual booting guides that showed that Windows XP was installed first. Thanks in advance.

---

### Post by Leppie on 2010-06-30
yes, you can re-install grub after you installed xp onto your machine booting off an ubuntu livecd.
the commnands to issue are:
```
sudo mount /dev/sda5 /mnt  ## replace /dev/sda5 with the root partition of your ubuntu install
sudo grub-install --root-directory=/mnt /dev/sda  ##note that this is /dev/sda and not /dev/sdaX
```simple as that ;)

---

### Post by dbowlin17 on 2010-06-30
> **Leppie said:**
> yes, you can re-install grub after you installed xp onto your machine booting off an ubuntu livecd.
the commnands to issue are:
[CODE][sudo mount /dev/sda5 /mnt  ## replace /dev/sda5 with the root partition of your ubuntu install
sudo grub-install --root-directory=/mnt /dev/sda  ##note that this is /dev/sda and not /dev/sdaX/CODE]
simple as that ;)


this can easily be a complicated thing to do. maybe it is just my incompetence but still, it can be done quite easily.

---

### Post by oldfred on 2010-06-30
If you install your second windows to a primary partition you then can directly boot it. Otherwise your windows7 will still control boot of the XP.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

