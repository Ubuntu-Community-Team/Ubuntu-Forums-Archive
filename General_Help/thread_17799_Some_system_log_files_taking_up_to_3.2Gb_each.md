---
title: "Some system log files taking up to 3.2Gb each"
date: 2005-03-02
forum: General Help
---

### Post by stodge on 2005-03-02
Help! THe following system log files are taking up to 3.2Gb each and are not getting rotated:

-rw-r--r--    1 root     root     125795078 2005-03-02 18:57 kern.log
-rw-r--r--    1 root     root     125795776 2005-03-02 18:57 messages
-rw-r--r--    1 root     root     125798767 2005-03-02 18:57 syslog

They are full of lines like:

Mar  2 18:58:25 localhost kernel: nv_sata: Secondary device added
Mar  2 18:58:25 localhost kernel: nv_sata: Secondary device removed
Mar  2 18:58:25 localhost kernel: nv_sata: Primary device added
Mar  2 18:58:25 localhost kernel: nv_sata: Primary device removed
Mar  2 18:58:25 localhost kernel: nv_sata: Secondary device added
Mar  2 18:58:25 localhost kernel: nv_sata: Secondary device removed
Mar  2 18:58:25 localhost kernel: nv_sata: Primary device added
Mar  2 18:58:25 localhost kernel: nv_sata: Primary device removed
Mar  2 18:58:25 localhost kernel: nv_sata: Secondary device added
Mar  2 18:58:25 localhost kernel: nv_sata: Secondary device removed


When I booted up tonight, X wouldn't start as the disk was full due to these files - these three files were taking about 9Gb in total!

I thought these log files were rotated and purged automatically? Any ideas how to fix this?

Thanks

---

### Post by stodge on 2005-03-02
I tried disabling the SATA interfaces that aren't being used, but that didn't make a difference.

---

### Post by alastair on 2005-03-02
This had me stumped for a while - but a clue in :

/etc/cron.daily/sysklogd

Which runs "syslogd-listfiles" to determine files to rotate in /var/log (man syslogd-listfiles).

Is anacron running?

---

### Post by stodge on 2005-03-02
Ah no, it isn't. So that's what is responsible. I installed that and cronolog. So I'll see what happens.

Would be better to get a copy of the module with the warnings disabled.

Thanks :)

---

