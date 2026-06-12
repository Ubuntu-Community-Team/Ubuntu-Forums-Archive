---
title: "USB devices"
date: 2009-07-03
forum: General Help
---

### Post by amoya on 2009-07-03
Hello,

What does the system do when i plug a USB device in a USB port?
Which files does the system go to read?

Thank you in advance. 

Aldo

---

### Post by KeyserSoze93 on 2009-07-03
ubuntu uses udev to detect devices plugged in.

you could try checking out the files in /etc/udev/rules.d to see what kind of config is available.

---

