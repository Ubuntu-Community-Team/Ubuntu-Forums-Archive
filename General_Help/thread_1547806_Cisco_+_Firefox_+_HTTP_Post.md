---
title: "Cisco + Firefox + HTTP Post"
date: 2010-08-07
forum: General Help
---

### Post by spamalam on 2010-08-07
I am using the following software stack:
[LIST]
[*]Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2) (Kubuntu)
[*]cisco anyconnect vpn client 2.3.2016
[*]Mozilla Firefox 3.6.8
[/LIST]

The problem I have is that once I join my company vpn, I have full access to corporate services confluence, jira, servers, etc.  However when I use firefox to try and resolve a jira and post a body of text the connection timesout.

If i use any other browser it works fine, if slow, if i transition workflows it works fine, and if i use windows and firefox with the same cisco client it works fine.

This appears to be a specific issue with Firefox.  I have noticed that in general firefox is slower on ubuntu than on any other platform.

Any ideas?

---

### Post by lovinglinux on 2010-08-07
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by spamalam on 2010-09-24
Apologies for not getting back soon.

I have tried this, as well as completely disabling ipv6 however this has not solved the issue.

I've noticed some post actions do work, whilst others don't.

I have also seen that scping files never completes, I connect, the file is created on the target server inside the network but no data is ever transferred.  There's no problem at all under windows or mac (dirty).

---

### Post by spamalam on 2010-12-23
So in the end this turned out that one of the VPN servers was faulty, using a north american alternative worked.

---

