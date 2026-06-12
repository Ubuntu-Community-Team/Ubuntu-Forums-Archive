---
title: "Why gmail/hotmail won´t load on some networks?"
date: 2010-08-19
forum: General Help
---

### Post by carlos.hernandez on 2010-08-19
I have this problem, I have Ubuntu 9.10 and Windows 7 installed on my computer.
When I try to connect to hotmail in Ubuntu at my home network it never loads (says the connection was reset) but I can load hotmail in other networks using Ubuntu.
When I try to connect to gmail in Windows at my university´s network it won´t load, but I can connect to gmail at home...
This is the weirdest thing I´ve ever seen.
I decided to reinstall Ubuntu in the same partition from the scratch but it didn´t fix the problem either...

In the last weeks I´ve done 2 things: installed firefox branding in ubuntu as per update manager request and I also installed a wireless network at home, not sure which event might be causing the problem.
Any ideas?

---

### Post by lovinglinux on 2010-08-19
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

