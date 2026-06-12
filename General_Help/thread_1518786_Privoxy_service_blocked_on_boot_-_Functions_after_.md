---
title: "Privoxy service blocked on boot - Functions after a restart"
date: 2010-06-27
forum: General Help
---

### Post by zong1 on 2010-06-27
Dear all,

  I recently upgrade from 9.04 to 10.04.  Question is about a Privoxy installation.

System boots, and Privoxy started on in rc2.d / S20privoxy.   
However, the port 8118 was blocked even though the programme was attached to the port and listening as per lsof:
# lsof -i tcp:8118
COMMAND  PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
privoxy 1489 privoxy    1u  IPv6   5699      0t0  TCP localhost:8118 (LISTEN)

But cannot connect:
# telnet 127.0.0.1 8118
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

A quick restart of the programme, 
/etc/init.d/privoxy stop && /etc/init.d/privoxy
...And the problem goes away:
# telnet 127.0.0.1 8118
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
^]q
Yipee.

However, this is consistent on every boot. Rather strange.

Log files /var/log/privoxy/logdir do not mention a problem:
Jun 27 10:57:37.383 b78b68d0 Info: Privoxy version 3.0.15
Jun 27 10:57:37.383 b78b68d0 Info: Program name: /usr/sbin/privoxy
Jun 27 10:57:37.398 b78b68d0 Info: Listening on port 8118 on IP address localhost

I wondered if there was a programme that was afterwards afore it that may have got in the way, so moved S20privoxy to S199privoxy, but it made no difference.

ufw (iptables ), and portsentry are disabled on startup.

Any clues as to what is getting in the way.

Regards, z


PS. If this problem description is unclear, then please do not hesitate to ask for clarification in lieu of giving an answer. ;)

---

