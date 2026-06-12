---
title: "Sleep timer"
date: 2010-01-14
forum: General Help
---

### Post by HomoGleek on 2010-01-14
Can I set my computer to shutdown say after one hour?

---

### Post by sisco311 on 2010-01-17
> **DarrenTod said:**
> Can I set my computer to shutdown say after one hour?

Yes:
```
sudo shutdown -P +60 "The system is going DOWN to maintenance mode in 60 minutes!"
```
or
```
sudo shutdown -P 22:10 "The system is going DOWN to maintenance mode at 22:10!"
```

run:
```
sudo shotdown -c
```to cancel the shutdown.

read the man page for details:
```
man shutdown
```

If you need a GUI application, try [gshutdown]("apt://gshutdown") (click the apturl link to install it).

---

### Post by HomoGleek on 2010-01-17
> **sisco311 said:**
> Yes:
```
sudo shutdown -P +60 "The system is going DOWN to maintenance mode in 60 minutes!"
```
or
```
sudo shutdown -P 22:10 "The system is going DOWN to maintenance mode at 22:10!"
```

run:
```
sudo shotdown -c
```to cancel the shutdown.

read the man page for details:
```
man shutdown
```

If you need a GUI application, try [gshutdown]("apt://gshutdown") (click the apturl link to install it).
Perfect! 

TYVM :)

---

