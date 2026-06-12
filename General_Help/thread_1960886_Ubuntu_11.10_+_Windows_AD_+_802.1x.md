---
title: "Ubuntu 11.10 + Windows AD + 802.1x"
date: 2012-04-18
forum: General Help
---

### Post by teriyaki-89 on 2012-04-18
**Hi everybody. I am stuck with my ubuntu 11.10 connecting to network lan with 802.1x  and Windows 2008 AD authentication  **
I see the 802.1x security tab with my network connection, so that entering domain name and password does not help authenticate. 
I read one dude managed to connect to lan with 802.1x but what about ubuntu 11.10?
Am i missing something or some packages?

I suppose i have to join to domain first with samba or likewise-open5 or should it work without that?
I tested it with computer joined to domain by samba but winbind was on runlevel 99. On article people advised to move winbind to rc99winbind to work with domain but network starts before so ip does not assign
Or am i missing something?


Is there a normal article to solve this?  Cause i suppose many people're  afraid using linux on work because of such frustrating troubles with joining to corporate network
Is there a step by step to join ubuntu or linux to Windows AD+802.1X?

---

### Post by teriyaki-89 on 2012-04-19
what i got now that sometimes when i enter my data to 802.1x tab on network connection it get's ip address
but sometimes after restart not. Could anyone explain why it works so unstable or what to do to solve this problem ?

---

