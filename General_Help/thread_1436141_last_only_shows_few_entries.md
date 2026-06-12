---
title: "last only shows few entries?"
date: 2010-03-22
forum: General Help
---

### Post by firsttimeuser on 2010-03-22
i run the last command and noticed there are only a few entries, where can i find all the history logins? thanks

---

### Post by ajgreeny on 2010-03-22
Are you talking about your bash history, ie, the commands you have used in the past?

If so use ```
history
``` to show it in the terminal, or open the hidden file ~/.bash_history in your home, with gedit.

If you are asking about the command ```
last
``` that stores all the data in one of two log files /var/log/wtmp or /var/log/btmp, but only if they already exist.  If not you can make them with the touch command ```
sudo touch /var/log/wtmp
``` and it will then be used.

---

### Post by firsttimeuser on 2010-03-22
Thanks, i was asking the user login history, aka the "last" command.

somehow my system only shows the login history for the past 3 days, where is the older login history?  e.g. userA logged into the system 5 days ago from where.


> **ajgreeny said:**
> 
If you are asking about the command ```
last
``` that stores all the data in one of two log files /var/log/wtmp or /var/log/btmp, but only if they already exist.  

---

### Post by soltanis on 2010-03-22
They're in your PAM logs. You can look through

/var/log/auth.log

For a list of all authentications performed on your system. Programs like logwatch can automatically parse these for you and mail you periodic reports on user authentications, including failed authentications on your system.

---

### Post by sebastianabate on 2010-03-22
Check if logrotate gziped your log file 5 days ago ("last" only shows info from the actual log, not from the archived ones)

ls -l /var/log/wtm*

---

