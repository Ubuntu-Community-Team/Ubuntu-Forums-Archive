---
title: "Ethternet not working"
date: 2010-07-01
forum: General Help
---

### Post by s.v.z on 2010-07-01
Hi everyone!. Yeserday I ran the usual system update and when I turned my laptop on today, I saw that the ATI driver was not working. When I tried to reinstall it, I discovered that something has happened to my Ethternet too. I supposed that the reason was a wrong ip address (it actually was wrong). So I tried to fix it with the network manager. But after changing it to a good one, I can`t see any wired connections at all, though there is one for sure. I have deleted the connection and created a new default one, but still can`t see it.

---

### Post by dineshs on 2010-07-01
what is in```
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by s.v.z on 2010-07-01
it shows 
```
[main]
plugins = ifupdown,keyfile

no-auto-default=my:ma:ca:dd:re:ss

[ifupdown]
managed=false 
```

---

### Post by s.v.z on 2010-07-01
well, it has just begun to work.. probably, a miracle? =)

---

### Post by clrg on 2010-07-01
I sometimes experience problems with Network-Manager. Often, it suffices to

```
sudo service network-manager restart
```

then nm fixes itself.

If nothing helps, you can always manually start a DHCP request with

```
sudo dhclient <interfacename>
```

or assign a temporary IP address with

```
sudo ifconfig <interfacename> 123.124.125.126 netmask 255.255.255.0 
```

and define the standard gateway with

```
sudo route add default gw 123.124.125.1
```

Hope this helps as a quick-reference.

Greetings
ph

---

### Post by picbits on 2010-07-01
I've just had the same problem with my Revo - installed the automatic updates and the network wasn't working.


Rebooted and everything started working again

---

### Post by picbits on 2010-07-01
I've just had the same problem with my Revo - installed the automatic updates and the network wasn't working.


Rebooted and everything started working again

P.s. Not using Network Mangler

---

### Post by sahabcse on 2010-07-01
have you check the /var/log/messages and dmesg

---

### Post by akoskm on 2010-07-01
Hi!

My network card is configured with Network Manager too, but after the last update sometimes I can't reach some web address - the host what I'm trying to reach is up :confused:, I can ping/trace them from my local server.

What is the problem?

---

