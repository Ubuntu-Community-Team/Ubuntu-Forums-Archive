---
title: "configure rsyslogd to log to ssh session"
date: 2011-02-24
forum: General Help
---

### Post by sweberzerk on 2011-02-24
hi all,

I have a headless system I'm ssh'ing into. I would like to get the console logging from ryslogd sent to one of my sessions.
I've tried to edit /etc/rsyslog.d/50-default.conf to log to /dev/pts/0 (which usually is the tty of my first session it) and it works after I restart rsyslogd. But if I disconnect/reconnect my session (still the same tty) I need to restart rysyslogd again to get the log messages. It looks like it doesnt try to reopen the tty if it's been closed.

Can I fix it in the syslog config? The man page only says that "special tty handling is done" about ttys.

Or am I doing it the wrong way?

Thanks,

---

