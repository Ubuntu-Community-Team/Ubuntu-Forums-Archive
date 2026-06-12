---
title: "Beginner Help: Installed Ubuntu, Cannot Get Mail To Send Within Network"
date: 2010-12-16
forum: General Help
---

### Post by Mica_Koizumi on 2010-12-16
I'm a complete beginner to administrating my own box - and have installed Ubuntu 9.04 (Jackalope). 

I have it up and running - and have installed the applications that I needed.

However, I am unable to get mail to send within the network - I can send mail to external address, such as gmail, yahoo, etc, just not inside my work's network. This includes forwarding services such a spamgourmet - which redirects  to my work's email addresses.

Does anyone have any suggestions on potential set up issues I can check for? I am currently using Postfix as my email server.


note: this is what I found in the syslog:


Dec 16 13:55:55 mica-tools postfix/smtp[4248]: 9E014E409E: to=<mica@xxxxxxx.com>, relay=globala.mxsave.com[130.94.123.150]:25, delay=34, delays=0.02/0/33/0.28, dsn=5.7.1, status=bounced (host globala.mxsave.com[130.94.123.150] said: 550 5.7.1 <mica@xxxxxxx.com>,... Relaying denied (in reply to RCPT TO command))

---

### Post by gordintoronto on 2010-12-16
You don't need an email server, just an email program such as evolution.

I suggest you should use a version of Ubuntu which is currently supported, such as 10.04 or 10.10.

---

### Post by Mica_Koizumi on 2010-12-17
Apologies, I should have clarified. I am trying to send mail via Bugzilla - or even just via command line. This is where I am having issues.

Internal email fails whereas email sent to external addresses are sent with no errors.

---

### Post by efflandt on 2010-12-17
If you are trying to send mail "within" your network, why are you trying to use an external mail relay for it?

It has been years since I configured postfix. But if the domain in To: address does not resolve in local DNS as an A record to the LAN IP of your other smtp server, I believe you need to put something in **/etc/postfix/transport** to point to the local smtp server that handles mail for that domain.  And you would need that if you want to relay incoming public mail to that local server.

This is an old **transport** example from when I played around with postfix on my desktop and laptop:

```
wireless1.no-ip.com smtp:[wireless1.de-local]
```My local DNS resolved wireless1.de-local to my laptop's LAN IP.

Note that in **main.cf**:

```
myhostname = realhost.no-ip.com
# but I also had:
mydomain = de-local
relay_domains = wireless1.no-ip.com
```Likewise if you send local mail from the other server to the public name of the main server, the other server would need **transport** configured to send that to the LAN IP of your main server.

Note: no-ip.com no longer resolves "no-ip.com" subdomains for users, but does have other domain names for dynamic DNS.

---

