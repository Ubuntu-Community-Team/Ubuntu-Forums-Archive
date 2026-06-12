---
title: "how to kill a wine process?"
date: 2010-11-07
forum: General Help
---

### Post by sohlinux on 2010-11-07
How can I kill a specific wine process? for example paint shop pro has crashed under wine and will not close but how can I find the specific pid to kill it?


ps axwww | grep wine shows the pid of wineserver and winedevice but it doesnt show the pid of the prgram I want to kill

 5995 ?        Ss     0:00 /usr/bin/wineserver
 6001 ?        Sl     0:00 C:\windows\system32\winedevice.exe MountMgr                                      
 6054 pts/0    S+     0:00 grep --color=auto wine

---

### Post by sikander3786 on 2010-11-07
I have used System Monitor in the past to kill any wine program that went unstable.

You can also bring up the application launcher by Alt + F2 and type **xkill** and then click the unresponsive window.

You can also have a Force Quit applet on any of your gnome panel.

---

### Post by 3Miro on 2010-11-07
Wine has couple of processes like "wineserver" that deal with generic wine stuff. On the other hand the program itself has a process of its own. When I play Oblivion (or any other game), I have one "wineserver" process and a separate Oblivion process. You have to look for the the "paint shop" process:
```
 ps -e | grep paint 
```

---

### Post by sohlinux on 2010-11-07
> **sikander3786 said:**
> I have used System Monitor in the past to kill any wine program that went unstable.

You can also bring up the application launcher by Alt + F2 and type **xkill** and then click the unresponsive window.

You can also have a Force Quit applet on any of your gnome panel.

 :P Alt + F2  - xkill works a treat!

---

### Post by sohlinux on 2010-11-07
> **3Miro said:**
> Wine has couple of processes like "wineserver" that deal with generic wine stuff. On the other hand the program itself has a process of its own. When I play Oblivion (or any other game), I have one "wineserver" process and a separate Oblivion process. You have to look for the the "paint shop" process:
```
 ps -e | grep paint 
```

ps -e | grep paint or paint shop pro doesn't show any process neither does system monitor show specifically paint shop pro because it must be running inside the wine wineserver pid? anyway Alt + F2 - xkill does the trick.

---

### Post by I'mGeorge on 2010-11-07
xkill always does the job though some times you'll end up with a pretty messy desktop, like strange coloration or wrong resolution. But I guess this it's the price to pay for using wine

---

