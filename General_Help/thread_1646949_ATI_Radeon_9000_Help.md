---
title: "ATI Radeon 9000 Help"
date: 2010-12-16
forum: General Help
---

### Post by dexjjohn on 2010-12-16
I recently installed a Diablotek Radeon 9000 Video card and it will not boot into the system.  However, it just scrolls the screen with numerous errors.  I even tried inserting the installation media in the disc drive and the same error shows everytime.

I already changed the BIOS settings to use the PCI slot for video.

Ubuntu 10.04LTS installed.  Compaq

---

### Post by dexjjohn on 2010-12-16
I recently installed a Diablotek Radeon 9000 Video card and it will not  boot into the system.  However, it just scrolls the screen with numerous  errors.  I even tried inserting the installation media in the disc  drive and the same error shows everytime.

I already changed the BIOS settings to use the PCI slot for video.

Ubuntu 10.04LTS installed.  Compaq

---

### Post by dexjjohn on 2010-12-16
I recently installed a Diablotek Radeon 9000 Video card and it will not  boot into the system.  However, it just scrolls the screen with numerous  errors.  I even tried inserting the installation media in the disc  drive and the same error shows everytime.

I already changed the BIOS settings to use the PCI slot for video.

Ubuntu 10.04LTS installed.  Compaq

---

### Post by cariboo on 2010-12-16
Reboot, and when you are at the grub menu press [b]e/b] to enter edit mode, and add nomodeset to the end of the kernel line, and follow the instructions to reboot. If that works, you can make the change permanent by adding it to the end of the following line in /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash" 
```

be sure to include it inside the "" marks

---

### Post by ajgreeny on 2010-12-16
What video card did you use before?  You may need to delete your /etc/X11/xorg.conf if you were using one previously.

---

### Post by cariboo on 2010-12-16
Please don't create multiple threads on the same subject, I have merged your three threads.

---

### Post by dexjjohn on 2010-12-16
I was using my on-board graphics adapter .  Initially when I had the monitor hooked up it wouldn't even come on it would just flash and go off, then after I installed and changed my settings erroneous messages filled my screen.  The monitor that came with my computer is an old clunky CRT, however the computer itself is still good due to my upgrades every year.

---

### Post by dexjjohn on 2010-12-16
The bootloader fails to initialize....all i see are errors.

---

### Post by dexjjohn on 2010-12-17
So, nobody can help?

---

