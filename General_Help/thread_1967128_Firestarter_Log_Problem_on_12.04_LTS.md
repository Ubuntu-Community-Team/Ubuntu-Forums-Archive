---
title: "Firestarter Log Problem on 12.04 LTS"
date: 2012-04-27
forum: General Help
---

### Post by Michele S on 2012-04-27
[FONT=Verdana]Hello, when i launch firestarter i get this error:

Firestarter-WARNING **: Log file not found or access denied.
Firewall log monitoring disabled.

I followed this instructions:

[http://askubuntu.com/questions/52817/system-log-error-when-running-firestarter-configuration-program](http://askubuntu.com/questions/52817/system-log-error-when-running-firestarter-configuration-program)

editing (with "root" account) the file /etc/rsyslog.d/50-default.conf

from
[/FONT][FONT=Verdana]
#*.=info;*.=notice;*.=warn;\
# auth,authpriv.none;\ 
# cron,daemon.none;\ 
# mail,news.none -/var/log/messages 

[/FONT]  [FONT=Verdana]to

[/FONT]   [FONT=Verdana]*.=info;*.=notice;*.=warn;\         
auth,authpriv.none;\
cron,daemon.none;\
mail,news.none -/var/log/messages

Then i restarted rsyslog and also rebooted but i get the same message...

Can someone help me? [/FONT]

---

### Post by haqking on 2012-04-27
yes dont use firestarter, its an out of date and often buggy package.

IPTables is the built in firewall in Linux and most users use UFW or GUFW to manage it.

See here [Dangertux firewall guide in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1876124")

If you decide to go down this route then remove firestarter completely as it conflicts.

Peace

---

### Post by Michele S on 2012-04-27
I solved the problem. Before doing that steps i mentioned first, i created a dir:

sudo su
cd /var/log/
mkdir messages

Well, i thought that the log file has to be saved in the messages directory, but it was wrong, messages is the name of the log file.

Removing the directory i solved the problem:

rmdir messages
service rsyslog restart

:-)

---

### Post by haqking on 2012-04-27
> **Michele S said:**
> I solved the problem. Before doing that steps i mentioned first, i created a dir:

sudo su
cd /var/log/
mkdir messages

Well, i thought that the log file has to be saved in the messages directory, but it was wrong, messages is the name of the log file.

Removing the directory i solved the problem:

rmdir messages
service rsyslog restart

:-)

cool glad you got it working.

Peace

---

### Post by Michele S on 2012-04-27
> **haqking said:**
> cool glad you got it working.

Peace

Yeah, thanks! :guitar:

---

### Post by linuxcandy on 2012-08-11
Need to be root to restart rsyslog.

sudo service rsyslog restart


:KS

---

### Post by Molech on 2012-11-25
Ok.
Now I don't get more any error messages, but my events list is empty.
What now?

---

