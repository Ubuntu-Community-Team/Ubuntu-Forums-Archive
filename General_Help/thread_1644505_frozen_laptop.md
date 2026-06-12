---
title: "frozen laptop"
date: 2010-12-13
forum: General Help
---

### Post by adobenewt on 2010-12-13
I have a sony laptop that was working great with ubuntu 10. However after an update I restarted and now the desktop seems to be frozen every time I log on.

I've restarted many times and still the same. The arrow will not move and nothing happen with the keyboard. help.

Is there a fix or should i reinstall version 10 or reinstall a earlier version?

thanks!!

---

### Post by azertyh on 2010-12-13
hello,
see in your syslog if there are some error messages.
```
tail -f /var/log/syslog
```
see also
```
dmesg
```

---

### Post by adobenewt on 2010-12-13
how do i get there? i can't do anything at all. no keyboard and no mouse.

---

### Post by adobenewt on 2010-12-13
the keyboard works during start up before i log in to ubuntu

---

