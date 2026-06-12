---
title: "What replaced tail -f /var/log/messages in 11.10"
date: 2012-02-13
forum: General Help
---

### Post by chiques on 2012-02-13
I used to be able to use tail -f /var/log/messages

now it just hangs

Anybody know what the replacement is in Ubuntu 11.10?

---

### Post by efflandt on 2012-02-13
I wondered that at first too. The system log is now /var/log/syslog.

---

### Post by bab1 on 2012-02-13
> **chiques said:**
> I used to be able to use tail -f /var/log/messages

now it just hangs

Anybody know what the replacement is in Ubuntu 11.10?

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1728570") (post#2) to restore the messages.

---

### Post by chiques on 2012-02-13
I tried 
tail -f /var/log/syslog 

but it still hangs

---

### Post by chiques on 2012-02-15
It appears I have a solution:

```
tail -F /var/log/syslog 
```

will show a realtime log.

---

