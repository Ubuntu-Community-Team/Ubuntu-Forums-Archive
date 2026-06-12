---
title: "Default OS grub"
date: 2010-03-26
forum: General Help
---

### Post by panti19 on 2010-03-26
I installed Ubuntu on the entire disk, then resized it with gparted and installed XP, restored Grub2. everything is ok except that the defaul os it boots in is Ubuntu recovery mode.

how do i change that? i've tried opening grub.cfg but it has only one set default option and it's at the beginning, not after each entry..

thanks

---

### Post by Revolutionary101 on 2010-03-26
This might help:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by stinkeye on 2010-03-26
```
gksudo gedit /etc/default/grub
```

and change this line to reflect your choice 
```
GRUB_DEFAULT=[COLOR="Red"]0[/COLOR]
```
count the listings in your boot selection screen starting at 0

Then run```
sudo update-grub
```

---

### Post by efflandt on 2010-03-27
Or if you want the default to be whatever you selected the previous boot, change the /etc/default/grub entry to:

GRUB_DEFAULT=saved

before doing **sudo update-grub**

---

