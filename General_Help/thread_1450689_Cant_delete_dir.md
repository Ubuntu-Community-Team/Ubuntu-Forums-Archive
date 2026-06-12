---
title: "Cant delete dir"
date: 2010-04-09
forum: General Help
---

### Post by shade5 on 2010-04-09
Hi.

I used

```
mkdir mnt
sudo mount -o loop ubuntu-9.10-desktop-i386.iso mnt
```

and when I want to

```
sudo rm -r mnt
```

I get a "read only filesystem" error. 

The file ubuntu-9.10-desktop-i386.iso does not exist anymore. 

How can I delete this mess?

Thank you.

---

### Post by mcduck on 2010-04-09
did you umount the image before you tried to remove the directory?

---

### Post by shade5 on 2010-04-09
No. Since I deleted the image by accident. I restarted my system and now I could delete it. 

Case closed.

---

