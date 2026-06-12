---
title: "PC using 130MB of RAM while doing nothing"
date: 2011-03-04
forum: General Help
---

### Post by xxhopingtearsxx on 2011-03-04
My computer is using up 130MB of RAM.. while doing nothing. I thought it was Docky. I quit it. I thought it was Chrome, I quit it. I thought it was Gwibber. Quit it. 130MB of RAM while I only have System Monitor open. The top processes were Compiz at 9pm and Nautilus at 5pm. Nothing much.

I only have 512MB of RAM, too. Although for some reason, Ubuntu says I only have 494.4 MB of RAM (Windows 7 has at least 509MB useable).. But something is just wrong.

PS: I have UBUNTU 10.10. Maverick.
PSS: I have Intel 865GV chipset graphics card.

---

### Post by whatthefunk on 2011-03-04
That 130 MB is your system running.  If you had all 512 available, there would be a problem.

---

### Post by jerome1232 on 2011-03-04
You say it was doing nothing then mention closing 3 applications.

Honestly sounds about right, especially with a few apps open. (btw I understand chrome to be a bit heavy on the ram usage)


Gnome isn't the most lightweight Desktop Enviroment, if you are having performance issues (and you might with 512 ram) try a lighter Window Manager. There are alot of them around.

Like LXDE, Ice WM, Fluxbox, OpenBox, and etc...

---

### Post by mastablasta on 2011-03-04
lxde takes about 80MB ram
XFCE 100-120
Gnome 120-130
KDE i haven't tried yet.

---

### Post by xxhopingtearsxx on 2011-03-04
Alright, thanks guys. I'm using XFCE right now and it's doing fine.

Just for future onlookers:
```
sudo apt-get install xubuntu-desktop
```

> **jerome1232 said:**
> You say it was doing nothing then mention closing 3 applications.

I meant I had no programs opened, but I restarted and it did the same thing. I think you're right, it was Gnome. Using XFCE right now.

---

