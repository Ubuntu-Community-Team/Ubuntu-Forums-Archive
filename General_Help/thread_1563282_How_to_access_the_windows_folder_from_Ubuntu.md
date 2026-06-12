---
title: "How to access the windows folder from Ubuntu"
date: 2010-08-28
forum: General Help
---

### Post by Propheis on 2010-08-28
I have windows 7 Professional and Ubunto installed on my computer. how can i access my files from windows (eg photos) from my Ubunto OS?

---

### Post by tejashs on 2010-08-28
Ubuntu can perfectly read NTFS file systems and you can access them normally.
but if ypu have installed it using WUBI (ie inside windows) then say if you have installed it in D: drive then you cant read the contents of D: drive, but you can read contents of all the other drives.

---

### Post by bcbc on 2010-08-30
If you have wubi, then the "host" windows file system is accesible under the /host directory.

If it's on a different partition, you'll need to mount it first (look under the places menu).

---

### Post by meoconvn38 on 2010-08-30
It's automatic access to window partitions.

You can access buy click "Home --> List of Window Partitions".
:popcorn:

---

