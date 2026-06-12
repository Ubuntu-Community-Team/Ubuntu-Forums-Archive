---
title: "Blacklist mechanism of wireless card drivers"
date: 2011-04-28
forum: General Help
---

### Post by opipa on 2011-04-28
Under /etc/modprobe.d/,
I have four files could be related to my wireless card drivers(since I installed both b43 and wl for my Broadcom BCM4312 card),

```
broadcom-sta-common.conf
blacklist.conf
blacklist-custom
blacklist-bcm43.conf 
```

I am confused to how to do the blacklisting. However, I redundantly add blacklist line in almost every file, and it works(to toggle between wl and b43). Can anyone tell what is the way to do it?

---

