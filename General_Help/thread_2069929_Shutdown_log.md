---
title: "Shutdown log"
date: 2012-10-11
forum: General Help
---

### Post by sienile on 2012-10-11
I'm looking for a log file that shows what programs are running at shutdown and if a program hangs during shutdown.

I have this one program that constantly hangs, and shows up as an unknown program, during shutdown/reboot/log-off. I think there should be a log of the shutdown process, but I have no idea where to find it.

---

### Post by sienile on 2012-10-13
Solving another on my own. Tinkering keeps leading me to the answer days later... months in this case.

First, the messages log needs to be enabled. To do this edit **/etc/rsyslog.d/50-default.conf**. Uncomment the following lines:```
*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages
```

Logs will now be written to **/var/log/messages**.

---

