---
title: "Where are old log files stored.."
date: 2009-08-02
forum: General Help
---

### Post by shredder12 on 2009-08-02
I was vsftpd to share my stuff on LAN. In order to know how much of the data has been downloaded I used the logs present in /var/log/vsftpd* files.

whenever a new file is formed the old ones are transformed into vsftpd.log.[num] 

but after creating 5 such files... that is till vsftpd.4 whenever a new log files is created the oldest one i.e. vsftpd.log.4 jst disappears..

I need those logged information. Is there a way to stop the auto deletion of the log files..

---

### Post by TuckLive on 2009-08-02
I think you may be able to change that in etc/logrotate.conf or etc/logrotate.d

This link has some information that might help you more:

[http://www.cyberciti.biz/faq/how-do-i-rotate-log-files/]("http://www.cyberciti.biz/faq/how-do-i-rotate-log-files/")

---

### Post by shredder12 on 2009-08-02
thanks tucklive.. that worked..

---

