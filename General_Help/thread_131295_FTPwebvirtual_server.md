---
title: "FTP/web/virtual server"
date: 2006-02-16
forum: General Help
---

### Post by landlord on 2006-02-16
Hello.

Now that the box of infected bird crap is installed up and running with Ubuntu 5.10 a few questions and some problems arrised.

**Configuration.**
Static IP (from outside seen ip) from my DSL provider ---->>
-->>router with virtual server ports 21 and 81 enabled on wannabe ftp/web server port ---->>>
--->> inside i have dhcp enabled and also static ip with my server as a gateway (192.168.2.1) ---->>>
---->>>wannabe server has a static ip 192.168.1.57 

**What I did till now.**
-I installed proftpd wishing to put up a ftp server, i could not get it working configured the /etc/proftpd.conf file for anonymous access but from other computer in the network while trying to access the computer trough outer seen IP ([ftp://xxx.xx.xxx.xx](ftp://xxx.xx.xxx.xx)) i only got the identification request without being able to access the system with any password. after that i installed vsftpd, also not been able to configure the .conf file, since string options in file and in some help file on internet are very different.

**What I want to do.**
-First I would like some access from outside world trough terminal, rsh, whatever. how to enable all that. on router and linux?? than i want to enable ftp server. than i would like to have a web server for a website. after that the same machine will be used as a radius server for one or more wireless networks.




*I am very new to this environment (been working on HP-UX, Aix and Solaris) and any help, answers, links, good wishes - would be appreciated.*

Regards,
LL.\\:D/

---

