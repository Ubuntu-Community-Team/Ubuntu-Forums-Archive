---
title: "Rsyslog console output / Rsyslog rights"
date: 2010-11-26
forum: General Help
---

### Post by Ewgenijkkg on 2010-11-26
Hello, guys. I would like to forward the output of the emergency level log messages to the console of all users logged in. For that purpose, there exist the line 
 
```
 
*.emerg       *

```
 
in the standard rsyslog.conf file. However, no emergency messages are sent to my console:-( I asked some guys in the rsyslog-forum and the answer was that it has to have something to do with the priveleges dropping of rsyslog. There is a preveleges dropping of rsyslog indeed. In rsyslog.conf file I found the lines
 
```
 
$PrivDropToUser syslog
$PrivDropToGroup syslog

```
 
My question is now the following: Is that the reason for not sending the log messages to the console? Does the user "syslog" not possess apropriate rights for that purpose?
 
BR
Ewgenij

---

