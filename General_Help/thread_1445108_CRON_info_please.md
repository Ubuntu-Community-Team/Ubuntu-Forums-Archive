---
title: "CRON info please"
date: 2010-04-02
forum: General Help
---

### Post by macey on 2010-04-02
I know that I could find this if I searched enough buy someone here can
probably tell me quicker:)

Can anyone tell me where the cron tables are stored?

IE crontab -e (or -l)
and 

the system one :-
sudo crontab -e (or -l)

I need to retrieve them from a system backup, don't know where to look.

Thanks in anticipation..

---

### Post by irishbreakfast on 2010-04-02
excerpt from "man cron"
 "cron  searches  its  spool  area (/var/spool/cron/crontabs) for crontab files (which are named after accounts in /etc/passwd)"
and 
"cron  also  reads  /etc/crontab,  which  is  in  a  slightly  different format (see crontab(5)).  Additionally, cron reads the files in /etc/cron.d"

---

### Post by macey on 2010-04-02
> **irishbreakfast said:**
> excerpt from "man cron"
 "cron  searches  its  spool  area (/var/spool/cron/crontabs) for crontab files (which are named after accounts in /etc/passwd)"
and 
"cron  also  reads  /etc/crontab,  which  is  in  a  slightly  different format (see crontab(5)).  Additionally, cron reads the files in /etc/cron.d"

Thanks very much!

---

