---
title: "USB Flash Drives not mounting automatically"
date: 2010-04-24
forum: General Help
---

### Post by kantu on 2010-04-24
I have Ubuntu 9.10 and when i plug in my usb drive it wont mount it automatically and is not shown in the nautilus browser also, but if i search in /dev its visible(its detected) and i can mount using
mount /dev/sdc /mnt
But if i do this i can only copy files from browser and for all other times i need to use terminal again

---

### Post by _0R10N on 2010-04-24
Well, I'll try to guide you through simple steps.

First, run
```
cat /etc/fstab
```
Try to locate any line mentioning usb devices. If there's one, and the value "noauto" is detected, then change it to "auto". Restart the system and you're ready to go.

If there wasn't one, or the previous step didn't work, then you'll have to download some packages, by running
```
sudo aptitude install udev dbus-1 hal pmount
```
After that, you need to add your user to the plufdev group, by running
```
sudo adduser <your_username> plufdev
```

If there's a line for usb devices in your /etc/fstab file, then comment it.

I strongly recommend to backup any file you edit when modifying critical ones. In this case, you could make a copy of your /etc/fstab file
```
sudo cp /etc/fstab /etc/fstab.backup
```

Kind regards!

_0R10N >>

---

