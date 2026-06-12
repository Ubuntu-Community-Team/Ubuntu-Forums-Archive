---
title: "mount 2nd drive with terminal"
date: 2010-04-27
forum: General Help
---

### Post by spiky001 on 2010-04-27
Is there a command to mount 2nd hard drive from terminal, I dont need it permently also unmount, the drive is named if that helps?

---

### Post by Shazaam on 2010-04-27
Mount...
```
sudo mount /dev/xxxx
```
(where xxxx is the device/partition ie. sda or sda1 etc,)
Unmount...
```
sudo umount /dev/xxxx
```
(umount is NOT a typo).

---

### Post by bodhi.zazen on 2010-04-27
mount /dev/sdb1 /mount/point

mount LABEL=name /mount/point

See man mount

---

### Post by Shazaam on 2010-04-27
Sorry, forgot the mountpoint. Thanks bodhi.zazen

---

### Post by bodhi.zazen on 2010-04-27
> **Shazaam said:**
> Sorry, forgot the mountpoint. Thanks bodhi.zazen

You may use mount, without a mount point, so long as the mount is defined in fstab.

If it is defined in fstab you may either

mount /dev/foo

or 

mount /mount/point/foo

---

### Post by spiky001 on 2010-04-27
ok I seem to have done something wrong nautilus cant find my home?

---

### Post by spiky001 on 2010-04-27
ok fixed lost home. Still got problem with mount point not sure what to put tried 
```
sudo mount /dev/sdb1 /media/SPARE
```

dose not exist

---

### Post by bodhi.zazen on 2010-04-27
You need to create a mount point.

```
sudo mkdir /media/SPARE
```

---

### Post by spiky001 on 2010-04-27
thks for your help got there in the end

---

