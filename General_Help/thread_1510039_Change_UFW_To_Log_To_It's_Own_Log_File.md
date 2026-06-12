---
title: "Change UFW To Log To It's Own Log File?"
date: 2010-06-15
forum: General Help
---

### Post by DasFox on 2010-06-15
I'm running ufw-0.30pre1 on Slackware and it logs to /var/log/syslog and I wanted to know if I can make it log to it's own file, like /var/log/ufw?

THANKS

---

### Post by DasFox on 2010-06-15
Forgot to mention I'm using ulogd in Slack, where is like the "-j LOG" so I can change that to now,
"-j ULOG"



Ahh I THINK I have it looks like it's all in** /lib/ufw/user.rules**


[B]### LOGGING ###
-A ufw-after-logging-input -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-after-logging-output -j LOG --log-prefix "[UFW ALLOW] " -m limit --limit 3/min --limit-burst 10
-A ufw-after-logging-forward -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-logging-deny -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-logging-allow -j LOG --log-prefix "[UFW ALLOW] " -m limit --limit 3/min --limit-burst 10
-I ufw-before-logging-input -j LOG --log-prefix "[UFW AUDIT] " -m state --state NEW -m limit --limit 3/min --limit-burst 10
-I ufw-before-logging-output -j LOG --log-prefix "[UFW AUDIT] " -m state --state NEW -m limit --limit 3/min --limit-burst 10
-I ufw-before-logging-forward -j LOG --log-prefix "[UFW AUDIT] " -m state --state NEW -m limit --limit 3/min --limit-burst 10[/B]


Is that where all the logging is at in ufw?

What is the user6.rules about ipv6?

I have ipv6 in the kernel, but my user6.rules is empty?

THANKS


P.S. If I change all the -j LOG to -j ULOG so I can have ulogd log to a different log file and try to start ufw it won't. Gives me this error:
root@slackware:~# ufw enable 
ERROR: problem running ufw-init

---

### Post by dcstar on 2010-06-15
> **DasFox said:**
> I'm running ufw-0.30pre1 on Slackware and it logs to /var/log/syslog and I wanted to know if I can make it log to it's own file, like /var/log/ufw?

THANKS

This is a Ubuntu support forum for people that have problems with their Ubuntu-based systems, you should ask questions for other OSs in forums for those OSs:

General Help
All your general support questions for **Ubuntu, Kubuntu, Edubuntu and Xubuntu**.

---

### Post by DasFox on 2010-06-15
> **dcstar said:**
> This is a Ubuntu support forum for people that have problems with their Ubuntu-based systems, you should ask questions for other OSs in forums for those OSs:

General Help
All your general support questions for **Ubuntu, Kubuntu, Edubuntu and Xubuntu**.


ufw is a Ubuntu app that's why I'm asking the people that know the best... :)

But after a bit of Googling looks like it doesn't support ULOG... :(

---

### Post by maedox on 2010-06-15
On Ubuntu you can do pretty much anything with logging with syslog-ng. It replaces syslogd and the config is fairly easy to understand. You will most probably find lots of tutorials for it online.

---

### Post by DasFox on 2010-06-15
> **maedox said:**
> On Ubuntu you can do pretty much anything with logging with syslog-ng. It replaces syslogd and the config is fairly easy to understand. You will most probably find lots of tutorials for it online.


I use syslogd on Slack, so not sure there are any options here for me to do...


THANKS

---

### Post by bodhi.zazen on 2010-06-15
You are barking up the wrong tree.

You need to configure syslogd, not ufw

[http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)

---

### Post by DasFox on 2010-06-17
> **bodhi.zazen said:**
> You are barking up the wrong tree.

You need to configure syslogd, not ufw

[http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)


I'm not aware of any way in which you can do this with syslog. My understanding is you simply use ulog which is better.

---

### Post by bodhi.zazen on 2010-06-17
> **DasFox said:**
> I'm not aware of any way in which you can do this with syslog. My understanding is you simply use ulog which is better.

The tutorial I linked is for syslog, did you try it ? If so what problem did you have ?

You stated you are on Slackware and I am not sure if there are any slackware specific changes ...

Personally I use syslog-ng for these things (due to issues unrelated to this thread).

So, the bottom line, you need to configure your logging daemon, if you google search you will find more specific instructions.

You may also wish to ask on the Slackware forums (possibly Slax, Zenwalk, or related derivatives).

---

