---
title: "Crontab will not run"
date: 2011-05-07
forum: General Help
---

### Post by C23 on 2011-05-07
**EDIT: Never mind its working now..**

Hi, I'm running Ubuntu 10.10 x64 and after installing Cron commands they do not run.

Here is what I have installed using *crontab -e*
```
root@ccaudill:~# crontab -l
# m h  dom mon dow   command
0 7 * * * sh /home/minecraft/mcmap/day.sh
0 8 * * * sh /home/minecraft/mcmap/night.sh
* * * * * cp /home/minecraft/plugins/iConomyChestShop/ChestShop.stats.html /var/www/econ.html
root@ccaudill:~#
```The first two run a script that starts a program, the last is for copying  a simple webpage to the *www* folder once every minute.
After having these installed they do not run at all as far as I can tell.

---

### Post by hwttdz on 2011-05-09
Did you change anything?  Or was it working all along?  Mark as solved?

---

