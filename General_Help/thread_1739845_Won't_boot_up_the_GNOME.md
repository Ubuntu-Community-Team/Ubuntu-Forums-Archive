---
title: "Won't boot up the GNOME"
date: 2011-04-26
forum: General Help
---

### Post by tincan201 on 2011-04-26
.

---

### Post by zvacet on 2011-04-26
If you install that driver from system>admin>additional drivers try to remove it with

```
sudo apt-get --purge fglrx
```

Install driver from repos

```
sudo apt-get install xserver-xorg-video-radeon
```

---

### Post by tincan201 on 2011-04-26
.

---

### Post by lithopsian on 2011-04-26
If you install from the .run file, you should use *fglrx*-*uninstall*.sh to uninstall.  You'll find this inside the .run file.  Either you still have it from the install or you'll have to extract it again.

---

### Post by tincan201 on 2011-04-27
.

---

### Post by tincan201 on 2011-04-27
.

---

