---
title: "Application Monitor"
date: 2009-09-30
forum: General Help
---

### Post by castle on 2009-09-30
Hi all,
 
I've been using a program in windows called "Kiwi Application Monitor" (screenshoot is [here]("http://www.tucows.com/screenshot.html?id=600225")). It gives me some reports (for example: average CPU and memory usage, average running time per session etc).
I'm new to linux and I wonder if there is a tool like that for linux application? 
 
Thanks.

---

### Post by bogdan.veringioiu on 2009-09-30
Hi.
I don't know if there's something like kiwi, but try gnome-system-monitor.
Open a terminal, and type gnome-system-monitor. You can configure it to display a lot of useful info (technical).
Or, while in terminal, type top.
Bogdan

---

### Post by castle on 2009-10-01
> **bogdan.veringioiu said:**
> Hi.
I don't know if there's something like kiwi, but try gnome-system-monitor.
Open a terminal, and type gnome-system-monitor. You can configure it to display a lot of useful info (technical).
Or, while in terminal, type top.
Bogdan
 
Thank you for your reply. it is a good tool but it doesnt supply my requirement. I found the "time" command that gives me the process running time, but i also want to learn the average and peak CPU and memory usage for specific applications. "top" command can give the information but i couldnt get the info after the process killed. 
Actually I need that informations for statistical porpuse.
 
Can anyone help? Thanks...

---

### Post by Giblet5 on 2009-10-01
```
man sar
```

You can even use this to bill each user for cpu-seconds. ;)

---

