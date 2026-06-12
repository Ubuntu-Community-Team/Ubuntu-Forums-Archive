---
title: "GUI not loading"
date: 2009-11-28
forum: General Help
---

### Post by Bluetone on 2009-11-28
I have upgraded to Ubuntu 9.10 but have a problem in that the GUI doesn't load.

I ran the command below 

sudo dpkg-reconfigure xserver-xorg

which fixed it but the next day the same problem occured when booting my laptop. Anyone know how to permanently fix this?  Thanks

---

### Post by hirnwurscht on 2009-11-28
Hi Bluetone,

you have to deliver some information to make helping you easier.

What Graphic Card / Driver do you use?

When there is no GUI, do you only get a login prompt?

---

### Post by Bluetone on 2009-11-29
My Graphic card is

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

thanks

---

### Post by Virtual Liberty on 2009-11-29
Upgrading could have left the custom xorg.conf. Have you tried deleting it ?

```
sudo rm /etc/X11/xorg.conf
```

---

