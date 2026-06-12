---
title: "upstart for start mythtv-backend broken in 10.04"
date: 2010-05-08
forum: General Help
---

### Post by madhusker on 2010-05-08
any idea why upstart is broken in 10.04?  The old init of /etc/init.d/mythtv-backend start worked fine in 9.10.

$ start mythtv-backend
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.93" (uid=1000 pid=21758 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by ivanmacx on 2010-08-01
I'm sure this has been solved now, but just in case anyone else ends up here via Google like me, I had this problem because I forgot to run the command as root ie.

```
sudo start mythtv-backend
```

worked fine!

---

