---
title: "Problems with /dev devices since update"
date: 2011-06-13
forum: General Help
---

### Post by thecapsaicinkid on 2011-06-13
Media players cannot open /dev/dvd/ or /dev/sr0 it symlinks to (can browse disc in Nautilus though and the nodes exist) Sudo doesn't help, permissions look ok.

MythTV also falls over trying to access the devices in /dev/dvb/.

Any ideas?

---

### Post by FormatSeize on 2011-06-13
> **thecapsaicinkid said:**
>  Sudo doesn't help, permissions look ok.

Can you clarify what you mean by sudo doesn't help?
 
Also, have you tried to mount them manually? 
 
```

sudo mkdir /media
sudo mount /dev/sr0 /media

```
 
See if that helps out. Also, what version of Ubuntu are you using?
As for modification of the fstab file, I'll wait for someone else to come by and explain that process, as I don't deal with it much. I have in the past though, for the same issue. But it turned out that my computer was simply on it's last leg and stopped picking up the drives. The drives themselves still work, as I am using them in my newly built computer.

---

### Post by thecapsaicinkid on 2011-06-16
edit: seems to have been a bad disc, will look into dvb card separately.

---

### Post by KeyserSoze93 on 2011-06-17
If there's anything up with the symlinks in /dev, especially to CD-ROM drives, it's usually a problem with udev's cache of devices.

If you remove /etc/udev/rules.d/70-persistent-cd.rules and reboot then udev will recreate the symlinks and they should point to your existing devices. I've found this to be a problem if I replace CD drives, but it could also occur on an update.

Even if it's not your current issue it's worth noting.

---

