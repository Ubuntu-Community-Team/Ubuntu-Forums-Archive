---
title: "Viewing system error logs in 12.04"
date: 2012-09-04
forum: General Help
---

### Post by freesitebuilder on 2012-09-04
Recently did a clean install of 12.04 - where can I find system error logs if I need to view them? I'm sure I had a menu for this in 10.10, and I don't want to dig about too much and wreck my shiny new system straight away!

Thanks.

---

### Post by TheFu on 2012-09-04
I don't know how to do it in the GUI, but all the system log files are located in /var/log directory.
The most interesting for most needs are  syslog, messages, and auth.log.  Usually, I use grep to find specific parts of the files that are needed.

For example:
**$ sudo grep -i error /var/log/syslog**

Logs are protected from view by normal users since there is sensitive information inside.

---

