---
title: "how to refer to other computers on my home network by host name rather than ip"
date: 2012-06-13
forum: General Help
---

### Post by naftali mich on 2012-06-13
Hello, baby steps. I've a small home network up and running and managed to set up ssh. Can anyone tell me what to do to reffer to one computer on the network from another by host name rather than IP address (which is what I'm doing now)?

---

### Post by netopalis45 on 2012-06-13
You should be able to just replace the IP address with the host name in your command. 
ssh "host-name" 
The host name for the computer will show up when you open a terminal window. You will see "username@hostname"

---

### Post by bab1 on 2012-06-13
> **netopalis45 said:**
> You should be able to just replace the IP address with the host name in your command. 
ssh "host-name" 
The host name for the computer will show up when you open a terminal window. You will see "username@hostname"

Not quite.  You need to map the hostnames (or FQDN) to the IP address.  The most basic way is in the /etc/hosts file.  Each host has a /etc/hosts file.  You need to set all the mappings in each /etc/hosts file on each host in the network.  If you wanted to do this from one central location you can use BIND or DNSmasq.

Then you would get user@hostname at the prompt.  If you were to ssh to another host that the hostname would change.

The host I am at now is *malibu *so the prompt is **bab@malibu** if I ssh to another host (*kona*) then the prompt would be **bab@kona**

---

### Post by Aearenda on 2012-06-14
There is a local discovery capability that uses avahi (or bonjour on Macs, or on Windows computers with Apple's bonjour installed). You can usually simply append .local to the end of the name of your computers, and they will be found if they are on the same subnet. No editing of hosts files required for this, but it only works on the same subnet - which will usually be the case at home.

So for the user called 'mark' on the computer called 'pc1' you would type ```
ssh mark@pc1.local
```

---

### Post by naftali mich on 2012-06-14
thank you. that's perfect. I will also look into BIND and DNSmasq.

---

### Post by Habitual on 2012-06-14
easy answer:
edit /etc/hosts thusly:

```
xx.xxx.224.34    grid2
xx.xxx.224.62    c9Zabbix
xx.xxx.224.35    C9_Prod_Bacula
xx.xxx.224.53    c9gluster-nas1
xx.xxx.224.54    c9gluster-nas2
xx.xxx.224.36    Cirrhus9_Prod_sFTP
xx.xxx.224.38    Cirrhus9_Prod_Wiki
xx.xxx.224.47    MikeJ_WinServer 
xx.xxx.224.45    Cirrhus9_JJ_LAMP
```

HTH

---

