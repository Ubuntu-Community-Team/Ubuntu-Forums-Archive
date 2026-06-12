---
title: "rsyslog-mysql copy file to DB"
date: 2012-05-09
forum: General Help
---

### Post by skippercanfly on 2012-05-09
hi folks,

i have been trying for many hours and was not able to find a solution so i need some help plz.

i installed rsyslog-mysql and i followed this howto for the configuration. [http://en.tiagomarques.info/2011/03/rsyslog-config-in-ubuntu-10-10/](http://en.tiagomarques.info/2011/03/rsyslog-config-in-ubuntu-10-10/)

i managed to send the FW logs to rsyslog-mysql and store them to a seperate file and not syslog by adding this in /etc/rsyslog.d/50-default.conf

[B]:source, isequal, "ip address" /var/log/rsyslog/fw.log
& ~[/B]

my problem is that i cannot find how to copy the content of /var/log/rsyslog/fw.log to the database :(
currently is copying just the content of /var/log/syslog to the database

any ideas?

---

