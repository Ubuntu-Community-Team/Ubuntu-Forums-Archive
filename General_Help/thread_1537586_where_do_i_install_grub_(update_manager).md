---
title: "where do i install grub (update manager)"
date: 2010-07-23
forum: General Help
---

### Post by lue42x on 2010-07-23
i get this message and i dont know what to do :(

[http://img713.imageshack.us/img713/7418/screenshotui.png](http://img713.imageshack.us/img713/7418/screenshotui.png)

---

### Post by oldfred on 2010-07-23
You want to install to the drive which is sda, not a partition sda1. 

Partitions can only be used for advance configurations with another boot loader and are less reliable used that way. You would not be able to boot if you just install to a partition.

---

