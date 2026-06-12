---
title: "urgetn help needed..partitions disappeared"
date: 2009-09-06
forum: General Help
---

### Post by sudoomar on 2009-09-06
hello

my computer was shut down due  to electricity blackout
now i have hp laptop
i put my ubuntu jaunty live cd... it runs ok but it does not see my partitions (i had 2)
i am using QParted but it just gives me one unallocated partition

please help me

---

### Post by sudoomar on 2009-09-06
any ideas..i am desperat

---

### Post by P4man on 2009-09-06
Qparted? did you mean Gparted?
If you did use qparted, its stone age old, and doesnt support Ext4 if you where using that. USe gparted instead, its on the cd (system > administration > partition editor).

If you did use gparted.. then.. you have a problem.

try testdisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If you got crucial data on that laptop, I would advice to make a bytecopy of your drive to an external disk using dd before attempting to recover the partitions (you can use dd to image the drive even if you can't mount the partitions). Then install testdisk in a live session, and hope for the best

---

### Post by sudoomar on 2009-09-06
well sorry yess i used Gparted...

i will try your link Test disk and post back

---

### Post by sudoomar on 2009-09-06
> **P4man said:**
> 

If you got crucial data on that laptop, I would advice to make a bytecopy of your drive to an external disk using dd before attempting to recover the partitions (you can use dd to image the drive even if you can't mount the partitions). Then install testdisk in a live session, and hope for the best

can you elaborate more please?

---

### Post by P4man on 2009-09-06
which part :)

do you have an external drive same size or bigger as the harddisk in the laptop, to make an image? If so, you can make an image using

dd if=/dev/sda of=/media/diskwhatever/image.img

It will take a long time, and no output is given until its done, but it makes an identical copy or your drive, should you mess up with testdisk.

As for testdisk, enable the universe repositories (system > adminstration > software sources. Then you can install it with 

```
sudo apt-get install testdisk
```

As for how to use it, plenty of tutorials on the web and on testdisk's homepage.

---

### Post by sudoomar on 2009-09-06
> **P4man said:**
> which part :)

do you have an external drive same size or bigger as the harddisk in the laptop, to make an image? If so, you can make an image using

dd if=/dev/sda of=/media/diskwhatever/image.img

It will take a long time, and no output is given until its done, but it makes an identical copy or your drive, should you mess up with testdisk.

As for testdisk, enable the universe repositories (system > adminstration > software sources. Then you can install it with 

```
sudo apt-get install testdisk
```

As for how to use it, plenty of tutorials on the web and on testdisk's homepage.

ok i will get an external disk..i need more than 260 GB..will try and post back
thanks a lot for ur help

---

