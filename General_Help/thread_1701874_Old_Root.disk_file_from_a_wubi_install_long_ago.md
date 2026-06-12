---
title: "Old Root.disk file from a wubi install long ago"
date: 2011-03-07
forum: General Help
---

### Post by OFC on 2011-03-07
A long time ago I installed Ubuntu through Wubi, and I recently found the root.disk file and want to view the contents because there are some files on it I lost and really would like to get back. But, I have no idea how to open it.. Does anyone know how to?

---

### Post by kiyop on 2011-03-07
Boot with Ubuntu LiveCD.

Mount partition where root.disk exists by, for example, clicking right place from "Places".

Open terminal,
"Application" -> "Accessory" -> "Terminal"

$ sudo mount -t auto -o loop,rw [COLOR=red]<Path of root.disk>[/COLOR]/root.disk /mnt
$ sudo nautilus /mnt

---

### Post by Rubi1200 on 2011-03-07
kiyop's method is one way of doing it, but there is an easier method.

You can use [ext2read ]("http://ext2read.blogspot.com/")to recover any important data from the Ubuntu root.disk from within Windows.

---

