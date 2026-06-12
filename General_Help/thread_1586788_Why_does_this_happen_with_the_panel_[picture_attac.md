---
title: "Why does this happen with the panel [picture attached]"
date: 2010-10-02
forum: General Help
---

### Post by GammaPoint on 2010-10-02
I notice problems with the icons on my panel occasionally. For example, in this picture you can see what the weather icon, which normally is a full cloud, is only a partial cloud. Sometimes the power off button in the top right will be missing too. Anyone else had this problem?

[[IMG]http://img188.imageshack.us/img188/3443/screenshot1mc.png[/IMG]](http://img188.imageshack.us/i/screenshot1mc.png/)

---

### Post by andrewthomas on 2010-10-02
Your configuration must have gotten screwed up somehow.

You can set the panel back to the defaults with 
```

rm -r ~/.gconf/apps/panel
``` 
then add back your customizations

---

### Post by Quackers on 2010-10-02
Occasionally I only get half a wireless icon. As it still works I usually just leave it and at some time during the session it seems to fix itself.

---

### Post by spiky001 on 2010-10-02
Have you tried locking the panels? you can right click them and move them then lock to panel

---

### Post by Old_Grey_Wolf on 2010-10-02
Yes, I have had the same problem. I unlocked the icons position on the panel (removed the check next to "Lock To Panel" by right clicking the icons). After rebooting, I haven't had the problem since doing that. I probably should check to see if there is a bug report; however, I am sure one already exists.

---

### Post by Aegluin on 2010-10-03
This happens often: The indicators get screwed up and some are only half visible or twice (messenger icon). I hope this will be fixed in the next release(s)...

However I found a work-around. After a reboot, it looks normal again, but you can also just right click on the panel, properties, check "show hide buttons", wait and uncheck it again.

---

