---
title: "Changing Default OS to Ubuntu"
date: 2010-01-23
forum: General Help
---

### Post by Cunnilingus on 2010-01-23
I recently installed Ubuntu Netbook Remix on my laptop (less than a week ago) and was just wondering how I can change my default operating system to Ubuntu. As of now, when I start my computer I find myself at a menu where I can choose between running Windows or Ubuntu. I wish for my computer to simply run Ubuntu by default instead of prompting me for the operating system I wish to use. Is this possible?

---

### Post by d3v1150m471c on 2010-01-23
look up gparted and use it to delete the windows partition.

[http://ubuntuforums.org/archive/index.php/t-502450.html](http://ubuntuforums.org/archive/index.php/t-502450.html)

---

### Post by Cunnilingus on 2010-01-23
I deleted the windows partition and yet when I start up my laptop it still asks if I want to use windows or ubuntu, did I do something wrong?

---

### Post by baddog144 on 2010-01-23
Try running 
```

sudo update-grub

```
In a terminal. That should update grub so it only thinks Ubuntu exists.

---

### Post by Cunnilingus on 2010-01-24
I ran that command in a terminal and received this:

Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda2
done

I thought I deleted the Windows partition but maybe I didn't? When I open up GParted /dev/sda2 is the only unallocated partition. Sorry for the load of questions, I do not know much about Ubuntu yet..

---

### Post by Saiko Berry on 2010-01-24
Do you have an XP CD in? >_>

---

### Post by Cunnilingus on 2010-01-24
Nope..

---

