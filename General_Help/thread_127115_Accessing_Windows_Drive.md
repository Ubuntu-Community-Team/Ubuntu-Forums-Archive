---
title: "Accessing Windows Drive"
date: 2006-02-08
forum: General Help
---

### Post by spyke01 on 2006-02-08
hi guys, i want to be able to access my windows drive through xmms and other apps, but its protected, i can easily do this and access the file

```

sudo su -
cd /media/hda1

```

How can i access this partition in the gui?

---

### Post by kaamos on 2006-02-08
```
sudo nautilus --no-desktop /media/hda1
```
If you don't want to restict the usage to root, look here [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by spyke01 on 2006-02-08
thanks m8 thats what i needed

---

### Post by lamego on 2006-02-08
Optionally instead of running nautilus as root you can setup the mount so that the partition gets accessible for everyone:
Just add umask=000 to the fstab options (sudo gedit /etc/fstsab) .

---

