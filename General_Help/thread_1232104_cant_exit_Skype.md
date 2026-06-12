---
title: "cant exit Skype"
date: 2009-08-05
forum: General Help
---

### Post by Gunch36 on 2009-08-05
Im on Ubuntu 9.04 and i have some problems With my Skype (version 2.0.0.72)
I tried to reinstall it, but nothing...
After a while my skype freezes. I can see all the contacts but when i send messages to someone it says:  This message is not delivered Yet. Then when im trying to exit it it wont work. Simply nothing happens. Then i must run "System Monitor" and Kill the Skype process. Then When i start Skype again i receive all the messages what have been sent when my Skype was fooling around.
I can not solve the problem and don't know where to look...

---

### Post by aallison05 on 2009-08-17
Ditto.  I'm having the same problem, also running 9.04.

Strangely enough I can't get the process to kill using system monitor.  I'm stuck with skype eating up 22% of my cpu until I reboot.

---

### Post by meho_r on 2009-08-17
For killing it, try with:

```
killall skype.real
```

And:

```
killall skype
```

---

