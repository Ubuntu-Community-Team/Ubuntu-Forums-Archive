---
title: "Firefox is slow when pandora is running"
date: 2010-07-20
forum: General Help
---

### Post by techguy30 on 2010-07-20
When I listen to pandora, firefox slows way down.  I have noticed that when pandora is running the Process name "plugin-container" will go to 30-40%.  Can any one help me.  Thanks

---

### Post by lovinglinux on 2010-07-20
Since Firefox 3.6.4, a new process, called **plugin-container**, runs whenever you use some plugins. This process is responsible for plugin isolation, which prevents the browser from crashing if the plugin itself crashes.

The high CPU usage is because of flash running in the plugin container. See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

---

