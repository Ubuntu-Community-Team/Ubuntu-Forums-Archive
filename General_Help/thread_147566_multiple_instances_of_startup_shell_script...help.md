---
title: "multiple instances of startup shell script...help"
date: 2006-03-20
forum: General Help
---

### Post by jms830 on 2006-03-20
I am running a shell script at startup

#! /bin/sh
#
/home/jordan/theme/wallpaper/change-bg 300 /home/jordan/theme/wallpaper


but it runs about 10 instances of the script/executable, i can see them in the system monitor. is there any way to make a something only allow one instance of the script, or to fix this problem?

---

### Post by schilcha on 2006-03-20
Try:
```

#! /bin/sh
ps -C change-bg || /home/jordan/theme/wallpaper/change-bg 300 /home/jordan/theme/wallpaper

```
In short, look if a process called "change-bg" is running already. If not, start it...
Haven't tested it though, so make sure it works the way you want.

The other thing is to lookup all places, where the script's started and remove the excess occasions. IMHO, this is the cleaner, but also the more cumbersome approach.

Good Luck!

---

