---
title: "Some apps run only under root"
date: 2011-11-27
forum: General Help
---

### Post by Ika-Ika on 2011-11-27
Hello.

I recently reinstalled my system, and this time put in on lvm partition. I don't know if this caused the problems but it would be my guess because I never had similar problems. Here are some of my problems:
-Ktorrent crashes the instant I click open or browse buttons
-Amarok displays splash screen and updates system settings forever
-Transmission can't download (displays some permission-related error).
I would treat it as separate problems if it wasn't for the fact that none of the above happens when I run the apps with sudo.

My disk setup is:
-80GB disk with a small (300MB) partition for bootloader and rest used for lvm
-320GB disk used entirely as lvm
-entire lvm space assigned to one volume group, divided into 3 partitions: root (5GB), swap (3.5GB) and rest allocated to home. All partitions are ext4.

My hardware:
Asus P5LD2 Deluxe motherboard
Intel® Pentium(R) 4 CPU 3.00GHz × 2
nVidia GPU
3,2 GB RAM DDR2
Both disks manufactured by Seagate

Now that I think about it, could it be caused by the "encrypt home folder" option that I enabled during setup?

---

### Post by BC59 on 2011-11-27
> **Ika-Ika said:**
> 
Now that I think about it, could it be caused by the "encrypt home folder" option that I enabled during setup?

The applications you mentioned have on Home their configuration files.
You should have the problem with more apps, Thunderbird, Firefox, Shotwell, LibreOffice, Banshee and more.

I don't know if the choice of encrypted home was so useful to compensate all these caveats. You should encrypt your swap as well to be more effective the whole encryption.

---

### Post by Ika-Ika on 2011-11-27
I think I found the problem. For some bizarre reason, my /home/.kde dir has permissions set to root only. When apps try to access it, things go bad. I tried running nautilus with sudo and changed permissions to /home/.kde but the subdirs and files didn't budge even when I tried clicking "apply to enclosed files". Switching everything manually is just too tedious, is there a command to do it?

---

### Post by WorMzy on 2011-11-27
This can happen when you run graphical applications with "sudo". Use "gksudo", (or "kdesudo" if you use kde instead of gnome) for graphical applications; only use "sudo" for commandline apps.

A quick fix would be to run

```
sudo chown -R $USER:$USER $HOME
```

(asuming you don't have any symlinks to system directories)

---

### Post by Ika-Ika on 2011-11-27
It worked! Both Amarok and Ktorrent work perfectly now. Thanks for the tips!

---

