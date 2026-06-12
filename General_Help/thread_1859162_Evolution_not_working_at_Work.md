---
title: "Evolution not working at Work??"
date: 2011-10-13
forum: General Help
---

### Post by vanhenryjr on 2011-10-13
First ubuntu only laptop for me-system 76 running ubuntu 11.04 using Evolution 2.32.2 for email. I have my Gmail account set up via IMAP and it works great at home over my wireless network (WEB protected) and has worked ok at public places via wireless guest accounts. At my place of employement I connect via a wireless guest account and cannot check my Gmail with evolution. I can check Gmail via webbrowsers.

My question is this a firewall or something preventing me from checking my Gmail via evolution? btw I did do a search on evolution in this section and did not see a similar problem/solution although i may have missed it among the 250 responses.

thanx in advance!
van

---

### Post by Nostalos on 2011-10-13
I would say the answer is most likely,  yes they are firewalling off your connection.   Usually policy for open wifi connections is that is is not unfettered access.  typically limited to http/https only and often times transparently proxied.

If you want to verfiy open a Terminal window and type

> telnet imap.gmail.com 993

If it just hangs then you are most likely firewalled and the firewall drops the packets.   If it comes back with an error of "administrativly prohibitied" then the firewall is reject your packets.    And if it comes back with "connection established"  then you have some other issue.


> ~$ telnet imap.gmail.com 993
Trying 209.85.225.108...
Connected to gmail-imap.l.google.com.
Escape character is '^]'.

---

### Post by vanhenryjr on 2011-10-14
You nailed it. Thank you for your help. 

I am not sure how I was supposed to figure it out via terminal, but I am trying to learn.

thanx again

---

