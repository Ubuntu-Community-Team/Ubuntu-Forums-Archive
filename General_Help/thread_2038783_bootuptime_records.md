---
title: "boot/uptime records"
date: 2012-08-07
forum: General Help
---

### Post by kurja on 2012-08-07
Does ubuntu keep a record of when it's been started and/or shut down? And if so, where might I find these records?

---

### Post by ranger1021994 on 2012-08-07
I think Ubuntu keeps a record of when it started
Just type :
> uptime
I dont know about shutdown logs


To view logs go to /var/log
All log files are stored there.


Also have a look here : [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by kurja on 2012-08-07
> **ranger1021994 said:**
> I think Ubuntu keeps a record of when it started
Just type :

I dont know about shutdown logs


To view logs go to /var/log
All log files are stored there.


Also have a look here : [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

thanks, uptime only displays the currently running uptime though, I would have been interested in history.

auth.log seems to contain data about when the system has been running, though.

---

### Post by newlinux on 2012-08-13
You could install uptimed and then use uprecords to see your historical uptimes. You can configure it to even email you when certain milestones have been met.

---

### Post by kurja on 2012-08-17
thanks.

---

