---
title: "Where's menu.lst?"
date: 2009-11-29
forum: General Help
---

### Post by Newuser1111 on 2009-11-29
Theres no menu.lst.


Could I install the older GRUB?

---

### Post by lisati on 2009-11-29
Are you using 9.10?

---

### Post by Newuser1111 on 2009-11-29
> **lisati said:**
> Are you using 9.10?Yes.

---

### Post by Leppie on 2009-11-29
9.10 comes with GRUB2 which doesn't use menu.lst but grub.cfg.

Hope this helps

---

### Post by Mr Nemo on 2009-11-29
There isn't a menu.lst anymore. Take a look at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275). To modify the grub menu at startup you need to create a custom file which isnt hard to do. Go to /etc/grub.d to find the files. Copy the list from grub.cfg and paste it into 40_custom. Modify the list how you want it and then save it as 6_custom within the grub.d file. Restart and the list order should change.

---

### Post by audiomick on 2009-11-29
you could read this:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Newuser1111 on 2009-11-29
> **Mr Nemo said:**
> There isn't a menu.lst anymore. Take a look at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275). To modify the grub menu at startup you need to create a custom file which isnt hard to do. Go to /etc/grub.d to find the files. Copy the list from grub.cfg and paste it into 40_custom. Modify the list how you want it and then save it as 6_custom within the grub.d file. Restart and the list order should change.Thanks.

---

