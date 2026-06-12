---
title: "Anyway to turn off bluetooth on boot"
date: 2010-01-04
forum: General Help
---

### Post by zine92 on 2010-01-04
I hate to say this but how do i disable bluetooth on boot up. I know bluetooth can be turn off manually everytime i on my com. But how do i permanently disable bluetooth on boot up. I don't want to disable it in bios because i am having dual boot.

---

### Post by spiderbatdad on 2010-01-04
```
sudo update-rc.d -f bluetooth remove
```

---

### Post by J V on 2010-01-04
system > preferences > startup programs

Disable bluetooth...

---

### Post by zine92 on 2010-01-04
Thankz a lot guys.

---

### Post by ajgreeny on 2010-01-04
If your machine has no bluetooth to use, you can uninstall it with synaptic, along with several other bluetooth packages.  Just be careful to note what dependencies are also removed as you could remove a lot of gnome apps with at least one of the bluetooth apps, libbluetooth3, and libgnome-bluetooth7 will remove gnome-network-manager as well; not what you want, probably.

Bum (boot-up-manager) can also be installed and used to stop bluetooth and several other un-needed services running.

---

### Post by zine92 on 2010-01-09
Anyway i did try that, my problem i think was because of the kernel, when everytime i on, the kernel will power up everything and therefore my bluetooth is on as well, tried disabling and the bluetooth light is still light on.

---

