---
title: "backup usb / restore to HD2"
date: 2009-09-03
forum: General Help
---

### Post by t_virus on 2009-09-03
hey all,
is it possible to backup ubuntu installed in a usb drive and recover to 2º partition of an HD?
first i installed ubuntu 9.04 to a usb drive (8Gb) but its very small for all i want.. so i installed ubuntu 9.04 to the second partition of my HD..
the question is if i can make a backup of the usb drive and restore it do my second partition of the HD (both with ubuntu 9.04).
thankz all

---

### Post by mike555 on 2009-09-03
Not sure if it will work , but you could try using gparted to copy one to the other ....

---

### Post by bumanie on 2009-09-03
It should work with gparted as stated above. Also, you could use dd commands such as dd if=/dev/sdx of=/dev/sdx
if=input file ie the drive you are copying from, you will have to add the correct drive letter in place of the x ; of=output file ie the drive you are copying to - again change the x to the appropriate drive letter. dd is very powerful, so if you get things mixed up you will probably wreck the present installation. Why not just make a new install on a bigger drive via the usb startup disk creator? It does a persistent install as far as I know - but maybe you should double-check first. Go to system --> administration --> usb startup disk creator. Of course after using gparted or dd commands, (if that's way you go), you will have to increase the partition size, otherwise, it effectively be the same size as before.

---

### Post by t_virus on 2009-09-07
hey guys, thanks for the replys, i got tired of trying to restore...
did a new HD instalation and its running fine. i&#7743; installing everithing as i nedd.
guess this is the best way of doing this.

thanks

---

