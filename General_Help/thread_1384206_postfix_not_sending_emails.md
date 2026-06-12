---
title: "postfix not sending emails"
date: 2010-01-18
forum: General Help
---

### Post by dattu on 2010-01-18
dear folks,

i'm not a techie but have tried my best to solve the issue without success. I have a static IP from local ISP and my computer is configured with 192.168.1.2 (LAN IP).

I have installed ubuntu server 9.04 and want to send emails from my server for which I've configured postfix. But I dont know what to do next.

My questions are:

1. Do i need to install DNS server for using postfix? If not, what should I install to send emails from this server?
2. Do I need to forward any particular port in my router?
3. If I dont have a fully qualified domain, what are the configurations I need to do to send emails?

please help!!!a

---

### Post by bsh on 2010-01-18
what do you mean by "want to send emails from my server"?
there are many different ways to "send mails". your server could act as a standalone mail server (which is quite complicated), or just be a "smarthost", that doesn't deliver mail directly to the recipients, but instead, just relays them to another mail server (ie. for the one provided by your isp). the latter is a lot easier. in both cases, you are "sending mail"... :)

port forwarding: sure. you need port 25 (default smtp port, often blocked by isp's to stop zombie smtp servers inside their own network), port 465 for smtps is optional, and port 587 can be used for both smtp/smtps, if enabled (this is useful if your isp is blocking port 25), of yourse you can use any other non-standard port for any of the above, if you want to use your postfix for your own private use only.

---

