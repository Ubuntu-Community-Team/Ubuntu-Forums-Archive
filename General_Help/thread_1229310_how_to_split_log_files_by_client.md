---
title: "how to split log files by client?"
date: 2009-08-01
forum: General Help
---

### Post by ruipedroca on 2009-08-01
Is this possible?: :confused:

I have a ubuntu log server and I'd like to know how can I make it create a specific log file for each client machine being logged.

I'm using sysklog, but I don't mind using other daemon like rsyslog.

---

### Post by ruipedroca on 2009-08-02
anyone?...

---

### Post by Johnny B on 2009-08-02
what about:
> cat logfile | grep $machine > $machine.log

---

### Post by ruipedroca on 2009-08-02
Thanks! It worked!!:

cat /var/log/syslog | grep $ddraytek.router > $var/log/draytek.log

Regards!!

---

