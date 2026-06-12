---
title: "/ect/apt/sources.list: no such file or directory"
date: 2011-03-08
forum: General Help
---

### Post by tdx-75 on 2011-03-08
Hi ive only ever had ubuntu for short periods of time but ive decided to switch over fulltime and get rid of windows. Im having a problem adding repositories to source.list
 for example with the iplist  this iw what i get from the terminal

tegan@ubuntu:~$ sudo wget [http://iplist.sf.net/sources.list.d/maverick.list](http://iplist.sf.net/sources.list.d/maverick.list) -O /ect/apt/sources.list.d/iplist.list
[sudo] password for tegan: 
/ect/apt/sources.list.d/iplist.list: No such file or directory

its not just with iplist its with a few other i have tried

when i type in 
gsku gedit /ect/apt/source.list 
it will open a window then immediately close

if i do manage to open it open in gedit it is blank

please help i havent quite figured this out yet

---

### Post by plucky on 2011-03-08
**etc not ect**

**gsku gedit /ect/apt/source.list** should be **gksu gedit /etc/apt/sources.list**

Be careful with spelling.

Good Luck

---

### Post by tdx-75 on 2011-03-08
oh wow that  was dumb mistake thanks man!!!

---

### Post by Snoman314 on 2011-03-08
What exactly are you trying to do?

if you're just trying to add the repositories
```
deb http://ppa.launchpad.net/ssakar/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/ssakar/ppa/ubuntu maverick main
```
into your sources list, you can use the gui if you'd find it easier.

System -> update manager -> settings -> other software(tab) -> click add, paste the lines in and hit enter.

---

