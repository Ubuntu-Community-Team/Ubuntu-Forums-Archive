---
title: "&quot;My Computer&quot;"
date: 2006-01-29
forum: General Help
---

### Post by aristotlewilde on 2006-01-29
I just installed Ubuntu 5.1 today and am having a blast learning it.  Is there something like My Computer in windows that will show system info such as installed RAM etc...?

I picked up an extra stick of RAM thsi week, and I can't tell if the system is recognizing it...

---

### Post by lnxpwr on 2006-01-29
the command "top" shows your mem, swap,cpu  and processes or if you wanna have something graphically than install xosview (sudo apt-get install xosview),,,

---

### Post by SlowHorse on 2006-01-29
You can find a lot of information about your system by "cat"ing information from your /proc directory.

For instance, if you want information on your memory, simply open a terminal and type "cat /proc/meminfo" without the quotes (""s). It will list the total amount of memory on your system, the amount of swap available, and some other cool stuff.

I'm sure there's a way to get this stuff from a GUI, but grabbing it from the terminal is more interesting. :)

---

### Post by CameronCalver on 2006-01-29
I just got the new ubunto 5.1 and installed the live cd it runs perfectly and then it says it could not install additional compontent and says there is  something wrong with the cd ??????? 

P.s if any1 has a used monitor ill buy

---

### Post by aysiu on 2006-01-29
If you want something graphical, Alt-F2 ```
gnome-system-monitor
```

---

### Post by engla on 2006-01-29
[QUOTE=aysiu]If you want something graphical, Alt-F2 ```
gnome-system-monitor
```[/QUOTE]
Why not just be nice and open it from the Applications menu > Admin/System Tools ?

---

### Post by ubuntu27 on 2006-01-29
[QUOTE=CameronCalver]I just got the new ubunto 5.1 and installed the live cd it runs perfectly and then it says it could not install additional compontent and says there is  something wrong with the cd ??????? 

P.s if any1 has a used monitor ill buy[/QUOTE]

LIVE CD??  Live CD is for testing or recovery, if you want to install Ubuntu Linux (or other Linux distro) use the INSTALL CD.

By the way, you say you installed Ubuntu already, and now you want to install the live CD?? I don't get it.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

