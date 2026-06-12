---
title: "BURG no themes, no keys woring."
date: 2012-10-01
forum: General Help
---

### Post by radolavv on 2012-10-01
Hello, I hawe this problem, that BURG is working in text mode, I cant change themes and the keys dont work.
Here is a link to an older post: [http://ubuntuforums.org/showthread.php?p=12228809#post12228809](http://ubuntuforums.org/showthread.php?p=12228809#post12228809)

---

### Post by daslinkard on 2012-10-01
> **radolavv said:**
> Hello, I hawe this problem, that BURG is working in text mode, I cant change themes and the keys dont work.
Here is a link to an older post: [http://ubuntuforums.org/showthread.php?p=12228809#post12228809](http://ubuntuforums.org/showthread.php?p=12228809#post12228809)
 The issue may be because of a recent GRUB update. You can reinstall burg to your boot drive. One fix was to do ```
sudo burg-install "(hd0)"
```And then run the update: ```
sudo update-burg
```Let me know if this fixes it for you.

---

### Post by radolavv on 2012-10-01
> **daslinkard said:**
> The issue may be because of a recent GRUB update. You can reinstall burg to your boot drive. One fix was to do ```
sudo burg-install "(hd0)"
```And then run the update: ```
sudo update-burg
```Let me know if this fixes it for you.
It didnt fix it, I tried reinstalling BURG a lot of times.

---

### Post by radolavv on 2012-10-05
Up.

---

### Post by elliotn on 2012-10-05
GRUB 2 supports themes and their pretty easy to instal than BURG

---

