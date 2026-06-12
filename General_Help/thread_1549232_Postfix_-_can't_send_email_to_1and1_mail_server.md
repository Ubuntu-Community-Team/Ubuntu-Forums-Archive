---
title: "Postfix - can't send email to 1and1 mail server"
date: 2010-08-09
forum: General Help
---

### Post by nightfever_pl on 2010-08-09
Hello,

Could you please help me investigate what do I need to change in postfix/ dns to send email to one one of the email server hosted by 1and1.

I'm using zenoss to monitor system/ network and devices. I wanted to setup email notification , so I installed postfix. All works fine when I use my private account on yahoo or hotmail. but when I specify email account that is hosted by 1and1 I receive error 421.
"

xxxxmyserver postfix/smtp[5399]: B0A5B22A06: to=<1and1emailaddress>, relay=mx00.1and1.co.uk[212.227.15.169]:25, delay=0.8, delays=0.04/0.02/0.62/0.12, dsn=4.0.0, status=deferred (host mx00.1and1.co.uk[212.227.15.169] said: 421 invalid sender domain 'xxxxmyserver' (misconfigured dns?) (in reply to RCPT TO command))

Could you please help me resolve this issue ?

Many Thanks,

---

### Post by efflandt on 2010-08-09
Does "xxxxmyserver" resolve to your public IP with an A record in public DNS, or is there a public MX record for that domain that points to an A record?

You are attempting to relay through a mail server that apparently does not use authentication and possibly cannot resolve the name your server identifies itself as, and/or your from address (spam trap?).  Easiest way to set that up is if your PC has a FQDN (hostname.domain) that resolves to its public IP.  If you have a dynamic IP you can still have a fixed name resolve to that (web search "dns hosting").  I have used no-ip.com for many years.  But many mail servers may still block "direct" mail from you based on known dynamic IP lists or reverse lookup (if the name contains "dial", "ppp", etc.).

It is possible that the relay only relays valid e-mail addresses for that ISP originating from their own network.

---

