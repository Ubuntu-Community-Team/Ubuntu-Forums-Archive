---
title: "How to read/write restricted folders?"
date: 2011-02-14
forum: General Help
---

### Post by Koffeehaus on 2011-02-14
Hello,
I just moved from using Linux Mint to Ubuntu. I'm trying to move files to a restricted folder, but I get the permission error. I was wondering how to open the folder as root? I remember in Mint you just right click and select 'open as root', but Ubuntu doesn't seem to have that option.

Thanks in advance,
Danny

---

### Post by wjz on 2011-02-14
Had a similar issue, this was my thread     [http://ubuntuforums.org/showthread.php?t=1685916s](http://ubuntuforums.org/showthread.php?t=1685916s)

---

### Post by JOHNNYG713 on 2011-02-14
In terminal  ```
gksudo nautilus
``` This will open Nautilus as super user !

---

### Post by oldos2er on 2011-02-14
```
sudo apt-get install nautilus-gksu
```, log out and log back in to see the 'Open as root' menu option.

---

### Post by Koffeehaus on 2011-02-14
> **oldos2er said:**
> ```
sudo apt-get install nautilus-gksu
```, log out and log back in to see the 'Open as root' menu option.

That works perfect. Thank you Oldos2er!!!

---

### Post by oldos2er on 2011-02-14
You're welcome.

---

