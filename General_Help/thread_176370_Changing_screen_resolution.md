---
title: "Changing screen resolution"
date: 2006-05-14
forum: General Help
---

### Post by GhandiBurger on 2006-05-14
my current resolution is 1024 x 768. I know my graphics card and monitor can go higher, up to 1680 x 1050. How can I change it to that resolution? (I have drivers installed)

---

### Post by endersshadow on 2006-05-14
Have you tried System>Preferences>Screen Resolution yet?

If so, what graphics card do you have?  Also, can you please copy your /etc/X11/xorg.conf file here so that we can better assess what the problem may be?

Thanks!

---

### Post by bluevoodoo1 on 2006-05-14
from the command line...

```
sudo dpkg-reconfigure xserver-xorg
```

and choose the correct driver and a higher resolution (as long as drivers are all set)

---

### Post by endersshadow on 2006-05-14
Do what bluevoodoo said first before doing what I asked.  Stupid mistake on my part.  Sorry!

---

### Post by GhandiBurger on 2006-05-14
Should I use the kernel framebuffer device interface?

---

### Post by GhandiBurger on 2006-05-14
double post. sorry. too many things going on at once.

---

### Post by GhandiBurger on 2006-05-14
Sorry for the triple post, but when I get to the screen where it says enable the screen resolutions, what keys do I hit to enable different resolutions? (how do I add the asterisk?)

---

### Post by bluevoodoo1 on 2006-05-14
[QUOTE=GhandiBurger]Sorry for the triple post, but when I get to the screen where it says enable the screen resolutions, what keys do I hit to enable different resolutions? (how do I add the asterisk?)[/QUOTE]


space bar.

---

### Post by GhandiBurger on 2006-05-14
mwuahahahaha!!! Thank you both for this. It is greatly apprieciated.

---

