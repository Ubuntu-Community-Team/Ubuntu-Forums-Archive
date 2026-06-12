---
title: "How to create a new log in /var/log/ ?"
date: 2011-03-28
forum: General Help
---

### Post by andygauvin.ee on 2011-03-28
Hi!

I'm running a server that has a number of services running that are all simultaneously logging to /var/log/[auth.log daemon.log kern.log] and the output I'm attempting to monitor is getting buried in the usual firehose of output from a very strict iptables and thwarted sshd breakin attempts.

My overall motivation is to get IPsec/L2TP running via xl2tpd.
IPsec is golden but I'm getting stuck trying to connect xl2tp to the right ports.. hence why I'm trying to watch its logs specifically.


Does anyone know how I can reroute the log output of these disconnected services to their own appropriate log locations?
eg, /var/log/sshd.log, /var/log/iptables.log, /var/log/ipsecd.log, and /var/log/xl2tpd.log?


Thanks Ubuntu community!

---

### Post by lloyd_b on 2011-03-28
> **andygauvin.ee said:**
> Hi!

I'm running a server that has a number of services running that are all simultaneously logging to /var/log/[auth.log daemon.log kern.log] and the output I'm attempting to monitor is getting buried in the usual firehose of output from a very strict iptables and thwarted sshd breakin attempts.

My overall motivation is to get IPsec/L2TP running via xl2tpd.
IPsec is golden but I'm getting stuck trying to connect xl2tp to the right ports.. hence why I'm trying to watch its logs specifically.


Does anyone know how I can reroute the log output of these disconnected services to their own appropriate log locations?
eg, /var/log/sshd.log, /var/log/iptables.log, /var/log/ipsecd.log, and /var/log/xl2tpd.log?


Thanks Ubuntu community!

I have no clue how to accomplish what you asked for - I believe the usual practice is to use 'grep' to look at the log, filtering out the stuff you don't care about:```
grep "sshd" /var/log/auth.log
``` to see only the entries from 'sshd'.

Lloyd B.

---

### Post by andygauvin.ee on 2011-03-28
> **lloyd_b said:**
> I have no clue how to accomplish what you asked for - I believe the usual practice is to use 'grep' to look at the log, filtering out the stuff you don't care about:```
grep "sshd" /var/log/auth.log
``` to see only the entries from 'sshd'.

Lloyd B.

Thanks Lloyd!
That's my current solution already but I'm looking for something more permanent, eg for intrusion detection at a glance.

Surely there must be some way to redirect the output of services to their own log locations...?

knightofthesun was looking for something similar, to no avail...
[http://ubuntuforums.org/showthread.php?p=10612183#post10612183]("http://ubuntuforums.org/showthread.php?p=10612183#post10612183")

---

### Post by blueridgedog on 2011-03-28
> **andygauvin.ee said:**
> Surely there must be some way to redirect the output of services to their own log locations...?


Though I suspect you have considered it, each service typically has a configuration file that allows you to specify logging options or start switch options for specifying logging options.

---

### Post by matt_symes on 2011-03-28
Hi

This thread is *kind* of similar to your request.

[http://ubuntuforums.org/showthread.php?t=1472593](http://ubuntuforums.org/showthread.php?t=1472593)

I have not read the attached pdf so i am not sure if it is what your are looking for but i thought i would pass it on just in case.

Kind regards

---

### Post by newbuntuxx on 2011-03-28
I don't believe you can re-direct logs to different files.

I have ufw, and to watch live logs i simply use tail -f and grep

like this:

```
tail -f /var/log/messages | grep "UFW"
```

Hope this helps.

---

