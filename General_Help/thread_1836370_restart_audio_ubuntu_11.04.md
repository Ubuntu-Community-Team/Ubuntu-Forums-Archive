---
title: "restart audio ubuntu 11.04"
date: 2011-08-31
forum: General Help
---

### Post by WinterMadness on 2011-08-31
tried the following:
```
joe@joe-laptop:~$ sudo /etc/init.d/alsa-utils restart
[sudo] password for joe: 
sudo: /etc/init.d/alsa-utils: command not found

```

seems outdated. wat do? :(

---

### Post by WinterMadness on 2011-09-01
?

---

### Post by nothingspecial on 2011-09-01
```
sudo alsa force-reload
```

---

