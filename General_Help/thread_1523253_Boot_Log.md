---
title: "Boot Log"
date: 2010-07-03
forum: General Help
---

### Post by daldude on 2010-07-03
Is there anyway to view the Boot Log of the messages displayed during the booting of Ubuntu?
I found log file viewer under Administration but there were so many logs I did not know if any of them were the Boot up logs.

I have my Ubuntu configured to display the messages as it boots before it switches to GUI mode and I see an error message about something failing to initialise but it goes by too fast to read the entire error message.

I have Ubuntu 9.04 64-bit

---

### Post by philinux on 2010-07-03
/var/log/messages or messages in the log file viewer.

Or from a terminal ```
dmesg
```

---

### Post by prodigy_ on 2010-07-03
> **daldude said:**
> Is there anyway to view the Boot Log of the messages displayed during the booting of Ubuntu?
Try /var/log/messages (and also /var/log/syslog as it's the most comprehensive of Ubuntu logs).

---

