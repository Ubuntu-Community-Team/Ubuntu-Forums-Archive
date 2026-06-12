---
title: "How to clone an Ubuntu PC exactly"
date: 2011-12-15
forum: General Help
---

### Post by cyberjar09 on 2011-12-15
Hello All, 

I have an Ubuntu pc configured exactly the way I like with all the necessary software installed and all the necessary configuration done. 

I would like to make exact duplicate clones of this PC using a flash drive. How would I be able to achieve this?  :confused:

Thanks.

---

### Post by Rodney9 on 2011-12-15
Clonezilla - [http://www.clonezilla.org/](http://www.clonezilla.org/)


Free Imaging software - CloneZilla & PartImage - Tutorial
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)


Rodney

---

### Post by sammiev on 2011-12-15
> **Rodney9 said:**
> Clonezilla - [http://www.clonezilla.org/](http://www.clonezilla.org/)


Free Imaging software - CloneZilla & PartImage - Tutorial
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)


Rodney

+1 for Clonezilla as I use a USB backup and love to play on the edge. Saved my sorry butt many of times as I know I can return to my last backup which I make on the weekly bases. :)

---

### Post by cyberjar09 on 2011-12-15
> **Rodney9 said:**
> Clonezilla - [http://www.clonezilla.org/](http://www.clonezilla.org/)


Free Imaging software - CloneZilla & PartImage - Tutorial
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)


Rodney

Wow thanks a ton Rodney9 .. much appreciated!

Thread marked as Solved

---

### Post by fdrake on 2011-12-15
how about "dd"
```

#clone the whole hdd to another hdd
dd if=/dev/sda of=/dev/sdb
#creat img of a hdd (in another hard-disk)
dd if=/dev/sda of=~/disk1.img
#create img of a partition, of course disk2.img is in anothe partition!
dd if=/dev/sda1 of=~/disk2.img

```

---

