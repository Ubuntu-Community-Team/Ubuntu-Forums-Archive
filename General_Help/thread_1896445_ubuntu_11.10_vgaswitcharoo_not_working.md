---
title: "ubuntu 11.10 vgaswitcharoo not working"
date: 2011-12-17
forum: General Help
---

### Post by Dans564 on 2011-12-17
in mint 11/ubuntu 11.04 i was able to use

```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
to disable my ATI graphics card. In mint 12/ubuntu 11.10 this returns

```
cat: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
```

This is an essential feature. Anyone know why it no longer works, and how can I fix it?

ps. Im gonna be traveling tomorrow so having this feature is much needed, otherwise my battery dies super quick  

thanks in advanced,
Dan

---

### Post by Dans564 on 2011-12-18
BUMP:

still no vgaswitcharoo anyone else experiencing the same problem?

---

### Post by Dans564 on 2011-12-19
got it! 
adding ```
modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

``` to /etc/rc.local fixed it

---

### Post by Dans564 on 2012-02-03
anyone have any idea why this doesn't work in 12.04 alpha 2?

---

