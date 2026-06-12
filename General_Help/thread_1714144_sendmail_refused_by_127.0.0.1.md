---
title: "sendmail? refused by 127.0.0.1"
date: 2011-03-25
forum: General Help
---

### Post by highspider on 2011-03-25
```
mailq
MSP Queue status...
        /var/spool/mqueue-client (2 requests)
-----Q-ID----- --Size-- -----Q-Time----- ------------Sender/Recipient-----------
p2P4vgcj002198       10 Thu Mar 24 21:57 [COLOR=Green]root               <--from terminal as root[/COLOR]
                 (Deferred:[COLOR=Red] Connection refused by [127.0.0.1])[/COLOR]
                     my@mail.com
p2P4pJgB000676       15 Thu Mar 24 21:51[COLOR=SeaGreen]www-data[/COLOR]      [COLOR=SeaGreen]<--- cgi-perl via a web page [/COLOR]
                 (Deferred: [COLOR=Red]Connection refused by [127.0.0.1])[/COLOR]
                     my@mail.com
        Total requests: 2
MTA Queue status...
/var/spool/mqueue is empty
        Total requests: 0



```send mail uses port 587 (my sendmail does)
```
netstat -nlupt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:[COLOR=Red]25[/COLOR]         0.0.0.0:*               LISTEN      630/sendmail-mta

```overkill to temp try and fix it
inbound port 587 opened firewall and router fowarding 
inbound port 25 opened firewall and router fowarding
inbound port 110 opened firewall and router fowarding

---

### Post by highspider on 2011-03-26
Grrr 
  port 25 was blocked by the ISP

---

