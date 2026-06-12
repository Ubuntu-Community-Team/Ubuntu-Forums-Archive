---
title: "Changing HOSTNAME need Help"
date: 2009-09-16
forum: General Help
---

### Post by Jeanprixx on 2009-09-16
Hi! i would like to ask why can't i access /etc/hostname comaand i already using administrative users "#"

but when i try to type /etc/hostname it replies with 

bash: /etc/hostname: Permission Denied.

i need to change hostname for some office PC. if you have better idea i can use i would appreciate it very much thanks.

---

### Post by Jeanprixx on 2009-09-16
Same Problem happens when i try to edit network interfaces using command line /etc/network/interfaces

---

### Post by P4man on 2009-09-16
those are files, not programs. If you want to edit them, you need to open them in an editor like nano or gedit. And you'll need to do so with admin privilidges. so for instance

```
gksudo gedit /etc/hostname
```

BTW, to change hostname, make sure you edit BOTH /etc/hosts and and /etc/hostname.

---

### Post by Francewhoa on 2010-03-12
There is an **easier, safer and faster** way to do this at [http://ubuntuforums.org/showthread.php?p=8955992#post8955992](http://ubuntuforums.org/showthread.php?p=8955992#post8955992)

---

