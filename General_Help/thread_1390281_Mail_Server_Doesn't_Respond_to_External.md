---
title: "Mail Server Doesn't Respond to External"
date: 2010-01-25
forum: General Help
---

### Post by graywalker on 2010-01-25
I have a Postfix / Dovecot mail server mostly set up and mostly working.  Its been a headache!  But, I have sent and received emails on my LAN, set up SquirrelMail to check email and all that good stuff.

However, it appears my server is not responding to external requests.

Internal : 
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:smtp                  *:*                     LISTEN      -               
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      -               
tcp        0      0 localhost:mysql         *:*                     LISTEN      -               

```
and from a LAN system
```

bobby@ubuntu:~$ telnet oodsong.graywalker.net
220 Oodsong.graywalker.net ESMTP Dragon Manor (Ubuntu)
ehlo oodsong
250-Oodsong.graywalker.net
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

mail from:<myemail@yahoo.com>
250 2.1.0 Ok
rcpt to:<bobby@oodsong.graywalker.net>
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
This is a test
.
250 2.0.0 Ok: queued as EBF361D8175
quit
221 2.0.0 Bye
```

BUT, from outside :
```
graywalker@ubuntu:~$ telnet oodsong.graywalker.net 25
Trying 74.171.36.69...
telnet: Unable to connect to remote host: Connection refused
graywalker@ubuntu:~$ telnet smtp.gmail.com 25
Trying 74.125.65.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP 14sm303428lgxk.14

```

Using Webmin 1.44, I look at the Networking ; Internet Services and Protocols and see that smtp doesn't have a program assigned - but if that were an issue, why can I send/received internally?

Do I need an extra entry in etc/hosts??

Oh, also - checked the Linux Firewall and it is set to allow all traffic.  My Router is set to pass smtp along to the mail server, my modem is set to pass smtp traffic along to the router. (both are set up as dhcp servers, so router is 192.xxx.xxx.x and passes out 10.x.x.x Ips to connected systems, including the mail server).

---

### Post by graywalker on 2010-01-25
Also get a Time out due to inactivity using [http://mxtoolbox.com/SuperTool.aspx](http://mxtoolbox.com/SuperTool.aspx)

---

### Post by lisati on 2010-01-25
Is your ISP blocking port 25?

---

### Post by jflaker on 2010-01-25
port25 is blocked by many ISP's to prevent hosting of mail servers....Improperly set up, it can be a spam relay host and could cause the ISP to be blacklisted and then NO ONE'S mail gets delivered.

---

### Post by graywalker on 2010-01-25
I can see them blocking OUTBOUND port 25, which they do and I've done a relay host with sasl auth to get around that, but blocking INBOUND smtp on port 25??  Especially since I have a static IP - AT&T's site CLAIMS that port 25 is not blocked with static IPs.

... on the phone with them now getting info on setting up a PRT. :D

---

### Post by jflaker on 2010-01-25
> **graywalker said:**
> I can see them blocking OUTBOUND port 25, which they do and I've done a relay host with sasl auth to get around that, but blocking INBOUND smtp on port 25??  Especially since I have a static IP - AT&T's site CLAIMS that port 25 is not blocked with static IPs.

... on the phone with them now getting info on setting up a PRT. :D

Outbound is not blocked as you would need that to communicate with other than your ISP's mail servers, like work or campus.  Inbound mail ports are likely blocked.  You would likely need to upgrade to business class service to get the inbound port limitations lifted.  

I am completely guessing, but with high speed internet, limitations must be used to keep the service usable.

---

