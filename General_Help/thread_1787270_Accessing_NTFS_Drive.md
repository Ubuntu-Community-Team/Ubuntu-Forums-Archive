---
title: "Accessing NTFS Drive"
date: 2011-06-20
forum: General Help
---

### Post by carmenat250 on 2011-06-20
I have an XP laptop which I booted up using an Ubuntu live CD.

When I'm in Ubuntu, is there a way that I can access files on the internal laptop XP drive which has been imaged as NTFS?

I thought there might be an option through places=>computer, but couldn't see a way.

---

### Post by entropy1 on 2011-06-20
When you click on Places you should see choices like "Computer" and "220 GB Filesystem" (or some such number of GB or MB) one of these filesystem type of choices will be your C: drive.  Smaller ones might be a recovery partition or startup partition that you don't want to mess with.

---

### Post by ruffEdgz on 2011-06-20
You will want to make sure you have the correct packages installed for using NTFS drives:
```

sudo apt-get install ntfs-3g

```
Once you have this, you should be able to mount the file system if Ubuntu doesn't automatically:
```

sudo mount.ntfs-3g /dev/sdaX /mnt/

```
The part "/dev/sdaX" is the path of your NTFS drive and you can the "/mnt" part to another location if you wish for the mount point.

---

