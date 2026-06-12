---
title: "start-stop-daemon logging"
date: 2009-07-17
forum: General Help
---

### Post by bigoperm on 2009-07-17
Does anyone know where the output of programs started with `start-stop-daemon` goes (both stdout and stderr)? Thanks

---

### Post by cariboo on 2009-07-17
All log files are located in /var/log, for daemons, /var/log/daemon.log

---

### Post by bigoperm on 2009-07-17
Mine is empty - is there a configuration? My /etc/syslog.conf is the default.

---

