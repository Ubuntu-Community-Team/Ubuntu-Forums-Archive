---
title: "VSFTPD won't restart"
date: 2011-07-17
forum: General Help
---

### Post by Palm&#279; on 2011-07-17
When I am trying to restart vsftpd, I get this:
```
kompas@kompas-System-Product-Name:~$ service vsftpd start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=2419 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```EDIT: It's now working, I just forgot sudo... Or something like that.

---

