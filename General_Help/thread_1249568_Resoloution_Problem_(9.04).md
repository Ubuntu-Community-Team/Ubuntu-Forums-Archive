---
title: "Resoloution Problem (9.04)"
date: 2009-08-25
forum: General Help
---

### Post by HpZ on 2009-08-25
just did a fresh install of ubuntu 9.04 using wubi. first thing I need to change is the resolution, but when I go to System>Preferences>Display it will not go above 800x600 and says the monitor is unknown. i've had 8.04 on this LAPTOP before and the resolution was fine.

been a while since i've used ubuntu so i could use some help. thanks.

---

### Post by tgeer43 on 2009-08-25
What graphics adapter does your laptop have in it?
Is the correct driver for it installed and activated under System->Administration->Hardware Drivers?

Let's start from there.

tgeer

---

### Post by P4man on 2009-08-25
if you get an nVidia or recent ATI card, then you want to install the drivers first, and that may well cure your problem. Go to system > administration > hardware drivers and check if anything is suggested.

If not, report back with the type of videocard you have. if you are unsure, open a terminal and type

```
lspci
```

edit: damn, beaten by less than a minute lol

---

### Post by HpZ on 2009-08-25
first thing i did was check drivers. nothing there except a wifi driver.

my card is nvidia geforce 7000M.

---

### Post by P4man on 2009-08-25
funny it doesnt suggest the restricted nvidia driver. Your card is supported by them

[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

So go ahead and give them a try. I think all you need to do is:

```
sudo aptitude install nvidia-glx-180 nvidia-180-modaliases
```

---

