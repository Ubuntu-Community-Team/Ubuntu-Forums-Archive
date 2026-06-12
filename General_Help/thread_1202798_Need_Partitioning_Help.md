---
title: "Need Partitioning Help"
date: 2009-07-02
forum: General Help
---

### Post by handyguy on 2009-07-02
Hello i currently are triple booting window 7, vista, and ubuntu.I have 2 hard drives in my dell and the second has space for all my shared storage partition and a dell utility partition with a media direct extended partition. I would like to install Fedora 11 but it seems like I will need an extended partition because installing from the live cd need you to have and ext3 for /boot and ext4 for / does anyone know how to make an extended partition larger or how to make one at all I have no problem with deleting the media direct partition but i need to keep the other ones intact. I attached a screenshot of my partitions.

---

### Post by michy99 on 2009-07-02
You can shrink sda3 and expand sda4 which is an extended partition, then create as many logical partitions as you need inside sda4.

---

### Post by handyguy on 2009-07-03
thank you for the help btw i am not leaving ubuntu just trying other distros

---

