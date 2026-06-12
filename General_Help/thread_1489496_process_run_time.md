---
title: "process run time"
date: 2010-05-21
forum: General Help
---

### Post by ub007 on 2010-05-21
I'm trying to find how long one of my processes is running and ended up with few confusions.

/proc/uptime --> this is the time I power on the machine and not the time OS actually boots, is that correct?

ps aux | grep my_app
 under START i get 08:45 , --> this time coincides with the time i powered on the machine, and not the time i actually started the app. any thoughts why that is so???

finally what is the best way to find how long my process has been running??

thanks in advance
david

---

### Post by Rubi1200 on 2010-05-21
If you want a nice program that gives you details about processes and their process time, CPU and memory usage, and other useful information, I suggest you install Htop. It is available either through Synaptic or the Ubuntu Software Center.

> /proc/uptime --> this is the time I power on the machine and not the time OS actually boots, is that correct? Correct

> ps aux | grep my_app
 under START i get 08:45 , --> this time coincides with the time i powered on the machine, and not the time i actually started the app. any thoughts why that is so??? Sorry, I don't know the answer to this.

---

