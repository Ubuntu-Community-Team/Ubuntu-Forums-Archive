---
title: "Can't log into Gnome"
date: 2006-03-22
forum: General Help
---

### Post by noumaan on 2006-03-22
I installed some software, uninstalled a few others turned off my computer. A few hours later I restart it and I have no GUI. 

I get logged into console/terminal with black screen and I don't know how to fix it. I am a very new user to ubuntu please help me.

---

### Post by dragomirov on 2006-03-22
It seems a X configuration problem. Tell us your graphic card along with your hardware and you xorg.conf (sudo vi /etc/X11/xorg.conf)

Then we can lend you a hand ;)

---

### Post by sands on 2006-03-22
try using the command "gdm" at console..
It starts Gnome from terminal..
Only root can do this.
So login as root..This can be done by "su" command
Then gdm..

---

### Post by aysiu on 2006-03-22
Type ```
sudo /etc/init.d/gdm restart
```

---

### Post by sands on 2006-03-22
s tis is a simpler one..
sudo /etc/init.d/gdm restart

---

