---
title: "Files locked"
date: 2010-05-03
forum: General Help
---

### Post by dbowlin17 on 2010-05-03
I want to use my flash drive, but I had files I put on using Ubuntu a few weeks back. Now I can only open them in read only copies and can't remove them, from the flash drive. I also have had some issues with file permissions on the hard drive. I was planning on reinstalling after a backup but now I don't know if that would be logical because the files might all be locked. I wanted to reinstall because I have issues with USB and these file issues. Any support would be helpful thanks

---

### Post by kouter on 2010-05-03
from terminal
```
gksudo nautilus
```

this will give you a root nautilus session, you can then change permissions on whichever directory you need to - simply right click and select properties -> permissions and set to whoever you would like to own it.

---

### Post by dbowlin17 on 2010-05-03
When I want to change the owner of the flash drive files to myself, it tells me that it is not possible.

---

