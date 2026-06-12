---
title: "External Monitor Settings not remembered"
date: 2010-04-30
forum: General Help
---

### Post by mathfreak123 on 2010-04-30
Hello, everyone! I installed Lubuntu for Lucid Lynx. I have an external monitor for my laptop, and whenever I log into lubuntu, both my external and my laptop monitor are turned on. I only want to use the external monitor, but my settings from last time are not remembered. Is there any way to get lubuntu to remember my monitor settings from last time?

---

### Post by mathfreak123 on 2010-04-30
Okay. Never mind. I solved the problem by adding

```
@xrandr --output LVDS1 --off
@xrandr -s 1920x1080
```

to the end of the my /etc/xdg/lxsession/Lubuntu/autostart file. :)

---

### Post by Anxious Nut on 2010-05-03
Almost same problem
100% same solution

Thanks for sharing the idea!!! :D

---

