---
title: "Problem with graphics and booting"
date: 2009-07-07
forum: General Help
---

### Post by static22 on 2009-07-07
Hi,

Im using ubuntu 9.04 and am running it on virtual box, everything was going fine untill me being stupid thought i would install the graphics driver. Ofc this didnt work and now when it boots i just get a big black screen and cant do anything.

I did have the virtual box guest addons installed, but the system still seemed a bit slow eg like when windows doesnt have a graphics driver in. So i thought i would try and put the ATI drivers in, this didnt click till i had done it.

Also i was having sound problems as well, it would sometimes work and other times not.

Any help would be appreciated, i just want to roll back or some how unstall what iv done. I dont really want to reinstall the whole thing again.

---

### Post by kandieyman on 2009-07-07
I made the same mistake when I upgraded my last laptop with a legacy ATI card. The solution is pretty straightforward if you did what I think you did. You likely installed fglrx, so you need to boot into single-user(recovery) mode and simply uninstall that package. That will fix your problem.

(Since you are using VirtualBox, maybe next time you can create a restore point before trying something with graphics. You may be very experienced, but I do that, and I've used Linux for 4 years.)

---

### Post by static22 on 2009-07-08
Sound mate, took about 10 min to find a solution.

1. Boot up in comand line nav to  /usr/share/ati/fglrx-uninstall.sh
2. Run script, wait for complete message, reboot enjoy :D


Thanks

---

