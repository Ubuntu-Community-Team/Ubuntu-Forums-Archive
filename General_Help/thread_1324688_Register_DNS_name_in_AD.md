---
title: "Register DNS name in AD"
date: 2009-11-12
forum: General Help
---

### Post by paf.goncalves on 2009-11-12
Hi!

I have my Ubuntu 9.10 configured to use DHCP from a win2003 AD domain controller.
I want to register the name of my machine in the DNS automatically.
In the win2003, in the zone properties i changed "Dynamic updates" to "Nonsecure and secure".

I already tried several combinations of the following properties in the /etc/dhcp3/dhclient.conf file with no result:
```

send fqdn.fqdn "kubuntu.domain.com.";
send fqdn.encoded on/off;
send fqdn.server-update on/off;

```
With "server-update off", i can see this message in the logs
```

dhclient: Unable to add forward map from kubuntu.domain.com. to 192.168.200.140: connection refused

```
I believe that with this setting (server-update off), dhclient should connect to the dns server and register it's name, and it should be allowed to do so, because dynamic updates are marked nonsecure in the dns server.
Is this correct ??

Any of you have experience with Ubuntu in AD environment ?

I wanted to install several Ubuntu machines in our company, but we have to work this out.

Paulo

---

### Post by paf.goncalves on 2009-11-16
No one :confused: ?????

---

