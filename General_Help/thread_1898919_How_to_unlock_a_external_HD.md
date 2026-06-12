---
title: "How to unlock a external HD"
date: 2011-12-22
forum: General Help
---

### Post by Da Flo-rid-eee-an on 2011-12-22
I just bought a Toshiba 320gb external HD. I'm not sure why but it is read only on my Xubuntu box, which is a problem because I need it to get the files off my Windows box. Anyways, I was wondering why the HD is read only, and how to get around it. - Thanks

---

### Post by bogyit on 2011-12-22
You need to install ntfs-3g, just run:
```
sudo apt-get install ntfs-3g
```
this will enable read/write for NTFS partitions. Bye :)

---

### Post by Da Flo-rid-eee-an on 2011-12-22
And it works, thank you!

---

