---
title: "Do I really need grub"
date: 2009-11-22
forum: General Help
---

### Post by duckleet on 2009-11-22
I have been a linux user for about 2 years and i don't use anything else can I take off grub and still boot up into my linux drive that I have.

I don't have windows and I am using ubuntu 9.10. The only reason I ask is that I need to speed up boot up.
I also would need to know how to remove grub if I can still boot.

---

### Post by SuperSonic4 on 2009-11-22
You don't have to have grub but you do need a bootloader of some kind - usually lilo.

You may be able to comment grub's timeout feature or change it to 0 in order to process


[http://wiki.archlinux.org/index.php/LILO](http://wiki.archlinux.org/index.php/LILO)

[http://wiki.archlinux.org/index.php/Grub](http://wiki.archlinux.org/index.php/Grub)

although grub2 is beyond me

---

### Post by mikewhatever on 2009-11-22
Grub is usually not the guy to blame for slow bootup. Get bootchart to get more info on what's taking the time.

---

