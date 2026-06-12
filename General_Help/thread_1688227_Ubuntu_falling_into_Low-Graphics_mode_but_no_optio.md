---
title: "Ubuntu falling into Low-Graphics mode but no options are working"
date: 2011-02-15
forum: General Help
---

### Post by jvacek996 on 2011-02-15
Hi, I recently uninstalled some unnecessary libs thinking that i could work around without them. it turned out i couldn't. so i installed every single one, and it seemed like everything was working fine.
but then i tried to boot, and was thrown into a low-graphics. well i tried to boot in a low-graphics environment temporarily but it turned out X just restarted. then i tried to reconfigure the settings, but choosing any option it threw me back into the last menu without any action being taken.
so i googled up some lines it was vomiting at me and it indeed might be my xorg not configured properly. but every time i try to reconfigure it and i look into the .conf file it turns out it is completely blank.
Maybe I should also note I am sporting a 64 bit bubuntu, not an NVidia though, Intel Series 4 express chipset family thing. I think it is a GMA4500MHD but not sure 
Therefore i turn to you, forum almighty, what shall i do so that i dont have to reinstall my beautiful pimped out system?

---

### Post by jvacek996 on 2011-02-15
Bump? anyone?

---

### Post by jvacek996 on 2011-02-19
oh come on. anyone?

---

### Post by Moyamo on 2011-02-19
Can you give more details please?

---

### Post by jvacek996 on 2011-02-19
I'm using a HP Compaq 6730s, usually triple booting W7 Ubuntu 10.10 and failsafe Vista using BURG, each is on it's own partition.
I am running Ubuntu in a 64bit environment.
When I boot into ubuntu i get the classic purple screen and then I fall into the low-graphics menu. When i choose boot ubuntu with low-graphics, nothing happens. If I go into the configure submenu, i cannot use the defaults, nor reconfigure nor used the backed up confs, it just goes back to the same sub menu once I click ok.
troubleshooting only prints some messages, restarting restarts, and the only thing that seems to work ok is the terminal. i tried some commands but they didn't seem to work, however i am still able to update and upgrade, wifi is miraculously working fine.

---

### Post by Moyamo on 2011-02-19
have you tried to reconfigure x

---

### Post by jvacek996 on 2011-02-19
That doesn't really sound familiar even though I tried to reconfigure xorg through some commands, copied It to /etc/X11 and renamed it to xorg.conf. When I did that, the reconfigure option finally started to work but it still didn't make it work after I rebooted, throwing me back into the groundhog menu if thats what you mean

---

### Post by Moyamo on 2011-02-19
```
$ sudo dpkg-reconfigure xserver-xorg

```

---

### Post by jvacek996 on 2011-02-19
Yeah, that one didn't seem to work. It aske me for my password since it is a sudo but then it didn't print anything and just thre me back to the $

---

### Post by Moyamo on 2011-02-19
How low is the low resolution mode.

---

### Post by jvacek996 on 2011-02-19
when I boot ubuntu normally and it tells me that I'm in low graphics? quite usual I think. 1280 times 1024 fully sharp, pictures are nice and normal as if i was in a normally booted one. Otherwise I get the terminal only sometimes as well, which is basically only terminal, nothing else

---

### Post by jvacek996 on 2011-02-19
Another shameful bump?

---

### Post by jvacek996 on 2011-02-22
Please let there be someone to give an end to my sleepless nights terrified with using W7 the other day.

---

### Post by Moyamo on 2011-02-22
[http://forums.techarena.in/operating-systems/1210660.htm]("http://forums.techarena.in/operating-systems/1210660.htm")

---

