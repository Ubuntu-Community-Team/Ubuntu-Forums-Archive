---
title: "Thunar: how to mount other partitions?"
date: 2010-06-16
forum: General Help
---

### Post by donsy on 2010-06-16
I'm experimenting with Xubuntu on a live CD and would like to access my Ubuntu files located on sda2. I don't see the icons in Thunar to I can mount other file systems. Is there a way?

---

### Post by nemiux on 2010-06-16
I'm not sure that Xubuntu is about the same as Ubuntu, but have you tried the easiest way, that is a code: ```
sudo mount -t ext3 /dev/sda2
```
? Sorry, if it didn't help

---

### Post by bodhi.zazen on 2010-06-16
I suggest you add the partitions you wish to mount inf /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ibbqalot on 2010-06-16
or you can install a partition program from the ubuntu software center
:popcorn::popcorn::popcorn:

---

### Post by donsy on 2010-06-16
So I take it there's no way to do it graphically as in Nautilus where you can simply click on an  icon to mount the file system?

---

### Post by donsy on 2010-06-16
Gigolo was what I was looking for. :p

---

