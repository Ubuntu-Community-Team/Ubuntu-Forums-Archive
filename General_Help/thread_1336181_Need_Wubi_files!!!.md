---
title: "Need Wubi files!!!"
date: 2009-11-24
forum: General Help
---

### Post by CrusaderAD on 2009-11-24
It happened. My wubi install now boots only to the sh:grub> prompt. I tried many of the solutions offered by the forum, none worked. Is there anyway to mount the wubi drive so I can at least get my files back?

---

### Post by howefield on 2009-11-24
Have you tried using a third party Windows utility to access your Ubuntu drive ?

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) can I access the Wubi files from Windows?

---

### Post by CrusaderAD on 2009-11-24
Neither program works. When I load the root.disk file in the disks folder, nothing comes up.

---

### Post by CrusaderAD on 2009-11-25
Here's a great way to retrieve your data, it was in the wubi guide:

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition: 

```
sudo mkdir /win
sudo mount /dev/sda1 /win
```

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

Change to the new vdisk directory and you should be able to view all your stuff. Whew... makes reinstalling a little less painful.

---

