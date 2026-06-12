---
title: "How can I improve my boot time?(bootchart included)"
date: 2011-08-13
forum: General Help
---

### Post by lordmonkeyu on 2011-08-13
Hello,
As in the topic. I would like to improve my boot time but I do not know how exactly do this. I have attached a graph from bootchart so that you can see what's going on while my PC is booting.

---

### Post by raja.genupula on 2011-08-13
its looking blur i am not seeing anything

---

### Post by TeoBigusGeekus on 2011-08-13
Nothing can be seen in your attached image; it's probably too large and it's been cut down.
However, you can disable startup services you don't want by going to Startup Applications and unchecking them (ubuntu one, assistive technologies, etc.)

---

### Post by raja.genupula on 2011-08-13
go with this [https://help.ubuntu.com/community/BootServices](https://help.ubuntu.com/community/BootServices)

---

### Post by haqking on 2011-08-13
a couple of simple changes:

gksu gedit  /etc/init.d/rc

change the line where it says CONCURRENCY=none to CONCURRENCY=shell

this improved by a few seconds for me.

It makes startup scripts run in paralel.

You may or may not get any imprtovement from this.

Also you can reduce boot menu delay by editing timout of menu.

If you are DHCP you can reduce IP address request times by adding a static if its possible for your configuration.

---

