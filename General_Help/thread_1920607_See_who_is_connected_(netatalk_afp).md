---
title: "See who is connected (netatalk afp)"
date: 2012-02-05
forum: General Help
---

### Post by hb108410 on 2012-02-05
Hi There,

I have set up ubuntu 11.10 as a quasi file server, sharing business files to colleagues and friends.

They are generally connecting via nettatalk to mac OS Lion.

Prior to me working on the system, (reboots, maintenance etc), is there a command I can execute to understand a) who is connected via netatalk / afp b) what is currently in session and being downloaded c) what has historically been downloaded from the server?

I am not using samba 
Cheers,

---

### Post by Khayyam on 2012-02-05
hb108410 ..

Netatalk logs to the 'syslog' facility if it is built with '--without-logfile'. This is currently the default with 2.x releases as the logging code is "partially broken". See the "Logging Options" section in [Chapter 5 of the Netatalk Manual]("http://netatalk.sourceforge.net/2.0/htmldocs/afpd.conf.5.html").

With 'syslog' afpd will log connections, errors, etc to /var/log/messages (or more selectively if your using [syslog-ng]("http://en.wikipedia.org/wiki/Syslog-ng"), [Metalog]("http://metalog.sourceforge.net/"), or what-have-you). These will be tagged in the logfile with 'afpd' and so can be parsed and/or monitored (with the likes of [Logwatch]("http://sourceforge.net/projects/logwatch/")). That covers a) and partially b) (as login is logged). c) on the other hand are not logged as aftp is serving the filesystem not the files (unlike ftp, http, and the like).

HTH ...

---

