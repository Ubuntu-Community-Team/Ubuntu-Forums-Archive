---
title: "how to stop password requirement when mounting volume"
date: 2009-11-17
forum: General Help
---

### Post by keevill on 2009-11-17
How do I auto mount an NTFS partition ?
I have my photos on this partition and when using Picasa, the folder has to be mounted requiring a password and then the folders added every time I restart the machine.
I do not require security on this volume and it's a nusiance to say the least that I have to go thru this performance every time I restart.
thx,
-keevill-

---

### Post by ciprian.topala on 2009-11-17
look for the program "storage device manager" (package name - pysdm)

---

### Post by P4man on 2009-11-17
not sure about the gui way to do this in kubuntu but just add the mount point to your fstab

Make a mountpoint

```
sudo mkdir /mnt/windowsdrive
```

```
kdesu kate /etc/fstab
```

Add a line similar to this:

```
/dev/sd[COLOR="Red"]a1[/COLOR] /media/windowsdrive ntfs-3g defaults,locale=en_US.utf8 0 0
```

replace sda1 with the correct partition.

---

### Post by keevill on 2009-11-17
Solved both ways are great !!
Thx !!

---

