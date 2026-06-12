---
title: "Gparted"
date: 2010-02-14
forum: General Help
---

### Post by Mr Nemo on 2010-02-14
Gparted live isnt recognizing my windows partition as mounted. How can I mount this partition so i can move space around.

---

### Post by bruno9779 on 2010-02-14
the fastest way is surely to right-click in Gparted (since you are already there) and choose mount.

---

### Post by Mr Nemo on 2010-02-14
I don't see any mount option

---

### Post by deanhopkins on 2010-02-14
Install ntfs-3g driver:

```
sudo apt-get install ntfs-3g
```

Make directory for drive to be mounted inside:

```
sudo mkdir /media/windows
```

Mount drive:

```
sudo ntfs3g /dev/sdxx /media/windows
``` 

(replacing /dev/sdxx with the correct number of your drive, you can find this in gparted, eg /dev/sdb1 or /dev/sda3)

---

### Post by mechro on 2010-02-14
If you want to "move space around" with Gparted then the partition shouldn't be mounted anyway.

By the way, this thread should be in one of the Support Forums. :D

---

