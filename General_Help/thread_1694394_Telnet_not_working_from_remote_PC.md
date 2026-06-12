---
title: "Telnet not working from remote PC"
date: 2011-02-24
forum: General Help
---

### Post by mswamy78 on 2011-02-24
[SIZE=2]Hello,[/SIZE]
[SIZE=2]
I am new [/SIZE]Ubuntu user. I have installed Ubuntu 10.10 Maverick Meerkat. If I want to connect from local m/c to ubuntu server using telnet it is not working. However telnet works If I can connect to any other linux m/c from Ubuntu m/c.

I tried "sudo apt-get install telnetd", but i got following message

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package telnetd


Please help

---

### Post by Chronon on 2011-02-24
```
user@localhost:~$ sudo apt-cache search telnetd                                                                                                   02/24/11  9:03 AM
[sudo] password for user: 
francine - feature rich ansi console login engine
heimdal-servers - Heimdal Kerberos - server programs
inetutils-telnetd - telnet server
krb5-telnetd - Secure telnet server supporting MIT Kerberos
pawserv - CERNLIB data analysis suite - distributed PAW and file transfer servers
telnet-ssl - The telnet client with SSL encryption support
telnetd - The telnet server
telnetd-ssl - The telnet server with SSL encryption support

```

---

### Post by gmargo on 2011-02-24
> **mswamy78 said:**
> 
I tried "sudo apt-get install telnetd", but i got following message
E: Unable to locate package telnetd

If you don't see **telnetd** it is probably because the **universe** repository is disabled.  Once you enable it you should be able to install telnetd.

To enable the **universe** repository you'll have to use either a convenient graphical tool or edit /etc/apt/sources.list.  See here for info:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Add_Extra_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Add_Extra_Repositories)

Be sure to run "apt-get update ; apt-get dist-upgrade", to bring yourself fully up to date too.

---

