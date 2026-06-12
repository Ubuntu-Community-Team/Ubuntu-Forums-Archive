---
title: "Can't open sudo gedit /etc/X11/xorg.conf"
date: 2010-07-15
forum: General Help
---

### Post by adam1611 on 2010-07-15
When I try to open sudo gedit /etc/X11/xorg.conf
by entering it in the "run tool" nothing appears...

what's wrong?

---

### Post by clhsharky on 2010-07-15
> what's wrong?
Nothing.
There is no xorg.conf file by default in Lucid.

Whats wrong that you need to use one?

xorg.conf will still work if you make one .

Sharky

---

### Post by adam1611 on 2010-07-15
I'm a complete noob on this....

I've installed Ubuntu 10.04 twice today.

The first time I installed it I had the xorg.conf file.
But this time, I don't have it...

I gonna insert some lines for my Razer copperhead mice

---

### Post by Nytram on 2010-07-15
use ***gksu*** for gui applications instead of ***sudo*** which is for terminal apps.

***gksu gedit /etc/X11/xorg.conf***

it will open a blank file because xorg.conf doesn't exist yet, where you can paste your code and then save it.

---

### Post by WorMzy on 2010-07-15
As Nytram said, use gksu. Using 'sudo' from the run dialogue will always fail (unless you check 'Run in terminal') because you have nowhere to enter your password.

---

