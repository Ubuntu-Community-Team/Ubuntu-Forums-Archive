---
title: "Help setting up Squid, please."
date: 2010-05-29
forum: General Help
---

### Post by kryth on 2010-05-29
For whatever reason I can not get my mind around this. I'm trying to setup a Squid transparent proxy server for my small computer repair business. I want to cache things like Windows Updates, and other sites/FTP that I go to all the time.I just want to save some bandwidth (and time). Heres my setup:


Router(to Internet)---->Ubuntu Squid Proxy--->Switch to 10-20 clients computer


Router is also acting as a DHCP server. It's IP address is 192.168.1.1

I've been banging my head against the wall. I don't if it's IPTables is giving me the problem or my other hunch is the client computers aren't able to talk to the DHCP server. Right now all I'm getting is APIPA addresses on the client machines. 

Any help, Before I smash my machine and cry?

---

### Post by dino99 on 2010-05-29
[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

[http://beginlinux.com/blog/2010/04/ubuntu-10-04-squid-proxy/](http://beginlinux.com/blog/2010/04/ubuntu-10-04-squid-proxy/)

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by kryth on 2010-05-29
Yeah, I had already read the last three links, and done the 'google thing'. I'm just mad ATM and can't figure out what I'm doing wrong. The first link seems even more complex (on first look)

---

### Post by kryth on 2010-05-29
oh, I've been using webmin also.

---

