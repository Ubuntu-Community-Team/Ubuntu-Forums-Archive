---
title: "Wubi fragmentation effects"
date: 2009-09-23
forum: General Help
---

### Post by J V on 2009-09-23
Installing ubuntu through wubi essentially restricts it to an NTFS file system, this gives it more chance to fragment ridiculously...

Will severe NTFS fragmentation have any performance effects?

If so, how do I defrag in ubuntu (Logically it should have no reason to defrag but with wubi it might)?

---

### Post by NightwishFan on 2009-09-23
I am not sure if you can, but there are several tools to do so in Windows, such as:

[http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

---

### Post by J V on 2009-09-23
Well I'm not so much worried about defragging the .disk file itsself, but the files *inside* it... (Presumably its the equivalent of a tarball?)

Or does ubuntu maintain a semi-ext filesystem within the .disk?

---

### Post by NightwishFan on 2009-09-23
I was just researching if it was an internal ext3, and I cannot seem to find out. My apologies. The WUBI help document only recommends the program I linked above.

---

### Post by J V on 2009-09-23
oh well, I guess I'll find out soon enough, thanks :)

Edit: Apparently the filesystem is installed as ext3, great news for wubi users :)

---

