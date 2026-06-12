---
title: "Where can I find logs about failed connection attempts"
date: 2011-05-15
forum: General Help
---

### Post by Martin_sensei on 2011-05-15
Hello,

I have a problem connection to an Android wireless hotspot, and I am trying to find any relevant logs to see what is happening.

Could anyone point me towards any such logs.

I can connect to other hotspots so I am looking for logs about errors when connecting.

Cheers

---

### Post by iponeverything on 2011-05-15
```
cd /var/log
tail -vf messages syslog debug dmesg

```

---

