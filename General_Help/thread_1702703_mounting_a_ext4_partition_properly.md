---
title: "mounting a ext4 partition properly"
date: 2011-03-08
forum: General Help
---

### Post by ELD on 2011-03-08
Hi all currently my fstab entry for a partition is this:

/dev/sda6  /media/Media   ext4     defaults                                  0  0  

But that seems to not give me any permissions on it, i can't create/copy/paste or anything with files onto it :(

Can someone tell me what's missing.

---

### Post by TeoBigusGeekus on 2011-03-08
```
sudo chmod 777 /media/Media
```

---

