---
title: "/var/log/messages right not set correctly"
date: 2010-12-24
forum: General Help
---

### Post by fipnova51 on 2010-12-24
Hello,

I have a problem setting the file permission for /var/log/messages.
It is currently set to *[COLOR=Blue]**-rw-r-----** 1 syslog adm 534 2010-12-24 10:36 messages[/COLOR]*

My problem is I'm using a monitoring tool (dedicated login) which cannot read this file so it always complains. Therefore everyday I need to run *[COLOR=Blue]chmod o+r[/COLOR]* messages on it.

My default file permission is umask 022 (in file /etc/profile).

I modified file *[COLOR=Blue]/etc/profile/syslogd[/COLOR]* by adding [COLOR=Blue]*SYSLOG_UMASK=022*[/COLOR] and restart the syslogd service (I ran command [COLOR=Blue]*/etc/init.d/syslogkd restart*[/COLOR] as ***[COLOR=Blue]root [/COLOR]***user) but it didn't change my file right.

Does anyone have a solution to permanently change my file permission.

Thanks & Happy Christmas.

-fipnova51

---

### Post by dcstar on 2010-12-25
> **fipnova51 said:**
> Hello,

I have a problem setting the file permission for /var/log/messages.
It is currently set to ```
-rw-r----- 1 syslog **adm** 534 2010-12-24 10:36 messages
```

My problem is I'm using a monitoring tool (**dedicated login**) which cannot read this file so it always complains. Therefore everyday I need to run ```
chmod o+r
``` messages on it.
.........

Put that account in the **adm** group.

---

