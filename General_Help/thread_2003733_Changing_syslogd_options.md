---
title: "Changing syslogd options"
date: 2012-06-14
forum: General Help
---

### Post by piriton on 2012-06-14
I would like to modify syslogd to startup with the following option from boot time.

Which file should I edit, and do I have to edit the apparmor profile due to the new flags ?

Also, any idea why the syslogd man pages are not installed by default ?
```

syslogd -m 0

```

---

### Post by kanikilu on 2012-06-14
I've not changed it myself, but I think the file you want is /etc/default/rsyslog. Not sure about the apparmor-profile, though...

---

