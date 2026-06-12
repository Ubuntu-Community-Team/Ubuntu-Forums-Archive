---
title: "can archives be deleted?"
date: 2009-08-17
forum: General Help
---

### Post by rifak on 2009-08-17
im wondering if everything in /var/cache/apt/archives/ can be deleted? it seems like it contains every .deb that ive installed and would like to clear up some space. thanks

---

### Post by michy99 on 2009-08-17
Yes, they can be deleted. From the terminal, enter```
sudo apt-get clean
```The only reason to keep them is if you need to reinstall packages and don't have a good internet connection.

---

### Post by HiImTye on 2009-08-17
or my personal favorite

sudo rm /var/cache/*/*

---

### Post by rifak on 2009-08-17
thanks!!

---

