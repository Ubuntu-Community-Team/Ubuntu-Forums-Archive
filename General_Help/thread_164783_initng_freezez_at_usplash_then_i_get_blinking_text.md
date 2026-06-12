---
title: "initng freezez at usplash then i get blinking text-light of death"
date: 2006-04-23
forum: General Help
---

### Post by cosmoshell on 2006-04-23
every tim i try to start ubuntu with initng im getting a little line at the top *looks at hand* left of the screen and nothing happens.

grate minds of ubuntu help me

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=cosmoshell]every tim i try to start ubuntu with initng im getting a little line at the top *looks at hand* left of the screen and nothing happens.

grate minds of ubuntu help me[/QUOTE]
I recently had this problem too. Make sure that you are using the latest version of InitNG. I fixed this problem by booting into recovery and then rebooting by typing "sudo reboot." Then that fixed it.

---

### Post by sinkxdie on 2006-04-23
Haha Master Chef thats exctly what i did :D

---

### Post by cosmoshell on 2006-04-23
dident seem to work me i still have the blinking textlight of death.

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=cosmoshell]dident seem to work me i still have the blinking textlight of death.[/QUOTE]
Did you set add GDM to the daemon InitNG files ? Try this in root terminal.

> sudo ng-update add daemon/gdm

---

### Post by cosmoshell on 2006-04-23
[QUOTE=MasterChief1234]Did you set add GDM to the daemon InitNG files ? Try this in root terminal.[/QUOTE]


Warning: "daemon/gdm" already installed in runlevel "default"
god@ubuntu:~$

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=cosmoshell]Warning: "daemon/gdm" already installed in runlevel "default"
god@ubuntu:~$[/QUOTE]
That's strange...I don't know why it won't work. The only thing I can recommend is to not use it or try rebooting into recovery mode again. Someone has to know the answer. Try looking in InitNG's bugzilla.

---

### Post by cosmoshell on 2006-04-23
[QUOTE=MasterChief1234]That's strange...I don't know why it won't work. The only thing I can recommend is to not use it or try rebooting into recovery mode again. Someone has to know the answer. Try looking in InitNG's bugzilla.[/QUOTE]
 where is initng's bugzilla??

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=cosmoshell]where is initng's bugzilla??[/QUOTE]
Look for it on [http://www.initng.org/](http://www.initng.org/).

---

### Post by cosmoshell on 2006-04-23
when i press the f key i get this instead of blinking light
[IMG]http://myspace-041.vo.llnwd.net/00680/14/07/680307041_l.jpg[/IMG
]

---

