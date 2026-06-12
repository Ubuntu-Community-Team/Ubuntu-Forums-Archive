---
title: "Zoneminder wont start"
date: 2012-01-07
forum: General Help
---

### Post by jimyhunt on 2012-01-07
Hello, I have installed Zoneminder on my mythbuntu box but when I run it get the following error

service zoneminder start
Starting ZoneMinder: Can't open log file '/var/log/zm/zmpkg.log': Permission denied at /usr/share/perl5/ZoneMinder/Debug.pm line 279.
failure

i have checked the zmpkg.log file:

01/07/12 19:49:21.300554 zmpkg[2016].INF [Command: start]
01/07/12 19:49:32.342530 zmpkg[2016].ERR [Unable to run "/usr/bin/zmdc.pl startup", output is "Starting server"]

I am unclear on what needs the permissions? (Me == Newbie)

---

