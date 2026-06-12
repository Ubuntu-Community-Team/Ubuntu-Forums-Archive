---
title: "regarding usb"
date: 2009-07-01
forum: General Help
---

### Post by becoolpal on 2009-07-01
sometimes i am not able to remove the contents of my pendrive 
what might be the reason ?
how can i format the pendrive ?
the pendrive has  ntfs format & i don't want to change its file system !!

---

### Post by fooman on 2009-07-01
> **becoolpal said:**
> 
how can i format the pendrive ?


you can use the partition editor (gparted)...if it is installed,  you will find it in system > administration > partition editor

if it is not there....install it by typing or copy/paste the following into a terminal:

```
sudo apt-get install gparted
```

---

### Post by colau on 2009-07-01
> **becoolpal said:**
> sometimes i am not able to remove the contents of my pendrive 
what might be the reason ?
how can i format the pendrive ?
the pendrive has  ntfs format & i don't want to change its file system !!
I think,you need read-write permission to remove something.
```

sudo apt-get install ntfs-3g

```

---

