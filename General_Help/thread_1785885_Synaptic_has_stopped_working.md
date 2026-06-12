---
title: "Synaptic has stopped working"
date: 2011-06-18
forum: General Help
---

### Post by garagestmarien on 2011-06-18
I can access synaptic via my unity 2D launch panel, from the apps menu and from system settings.
But today I went to use it and it won't launch.
I have tried to launch it with each of the above and each time to computer starts to do something and then stops. No freeze up, it just stops with the launch of synaptic.
I uninstalled it via software centre and re-booted. Then via software center I re-installed it, but it still doesn't work.
Helo :(

---

### Post by lidex on 2011-06-18
Try launching it from a terminal and post any error output here.

---

### Post by garagestmarien on 2011-06-19
Running sudo synaptic from terminal works.
Synaptic opens and I can install and un-install programs.
So I clicked to keep in launcher.
After I closed it, I tried the launcher, but it still will not open, only from terminal.

---

### Post by vanadium on 2011-06-19
Strange indeed, but (fortunately) not a fundamental problem. As Synaptic is not a program that you use every hour (or even day), you may reconsider from wanting it in the launcher. It remains very easy to launch when needed using the Supper key, then typing "syn" and pressing <enter>.

Might be some issue indeed with Unity.

---

### Post by lidex on 2011-06-19
Try this format in terminal:
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

---

### Post by jerrrys on 2011-06-19
make your own app launcher using the command "gksudo synaptic" and replace the broken one

---

