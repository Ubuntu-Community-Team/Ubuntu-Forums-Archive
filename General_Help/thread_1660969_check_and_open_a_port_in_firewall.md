---
title: "check and open a port in firewall"
date: 2011-01-06
forum: General Help
---

### Post by mahmoodn on 2011-01-06
1- How can I check if a port (or a range of ports) is open or closed in ubuntu firewall?
2- If I found it is closed, how can I open it?
3- If I open a previously closed port, does the system reopen it again upon system restart?

Thanks,

---

### Post by JeffDavidoff on 2011-01-06
I guess you are using the iptables firewall. If you are not familiar with the iptables command line I recommend you [Firestarter]("http://www.fs-security.com/"), a GUI for iptables. 

To check if a port is open or closed on the command line you can use the following command: 
```
sudo iptables -L -n
```This will list the current configuration. 

A good start is [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by mahmoodn on 2011-01-06
Thanks for your help especially Firestarter :)

---

