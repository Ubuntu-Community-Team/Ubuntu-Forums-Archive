---
title: "/etc/init.d/sysklogd missing!"
date: 2011-06-22
forum: General Help
---

### Post by linuxsyst on 2011-06-22
I need to change in file /etc/init.d/sysklogd SYSLOGD="" to SYSLOGD="-a /var/lib/named/dev/log" and then restart it.
but I can't find the file it's just not there.
:(:(:(:(:(:(
:confused:
Please help.

---

### Post by Helsvell on 2011-06-22
The main configuration file is now - /etc/rsyslog.conf and the last line of this includes the configuration files in the /etc/rsyslog.d/ directory.

I hope this helps.

---

