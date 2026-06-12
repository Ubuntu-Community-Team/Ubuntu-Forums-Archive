---
title: "DNS Problems"
date: 2010-12-04
forum: General Help
---

### Post by DeMus on 2010-12-04
Hi,
Since a few days I am experiencing DNS problems. It takes several seconds to find a webpage, where it was lightning fast before.
What happened?
I have a cable modem connected to a router(WAN) and this router(LAN) is connected to one PC directly, and to three others connected through to a switch.

I had to do a hard reset on the router because I could not log in anymore. I must have forgotten the correct password.
Now I have problems getting the correct settings in the router for DNS.

I tried my ISP's DNS addresses, but it is slow.
I tried Google's DNS addresses, but also those are not as fast as it was before the router reset.
I tried OpenDNS, and also here I have to wait.

When a Linux computer is connected to to router and the DNS addresses are put in the router, do I also have to write them in my Network configuration? Or should I write the address of my router here, or should I use full DHCP here?
Also, what should be in /etc/resolv.conf and in /etc/nsswitch.conf?

One note: as soon as the connection is made the data comes in at lightning speed, so it is not a slow connection problem. It has to do with DNS.
I use Google Chrome to browse the net and when I type or choose an address I see (in the tab button on top of the screen) a grey circular line rotating slowly CCW until it finds the address, then it becomes a white circular line rotating fast CW. This is when the page is loaded.

Who can help me to set things straight so I can surf the net without delays again?

---

### Post by DeMus on 2010-12-04
I know I should not bump the thread so fast but could somebody please help me with this DNS problem? What I have now is making my life a hell.

---

### Post by efflandt on 2010-12-04
Typically the router handles DNS for you, pointing to itself in DHCP on its LAN.  But some may simply proxy it (pass it on) or some may cache names for quicker lookup next time.

You could use Network Connections (or Edit Connections from network icon) to manually enter nameservers in Ubuntu to see if that helps.

---

### Post by DeMus on 2010-12-04
> **efflandt said:**
> Typically the router handles DNS for you, pointing to itself in DHCP on its LAN.  But some may simply proxy it (pass it on) or some may cache names for quicker lookup next time.

You could use Network Connections (or Edit Connections from network icon) to manually enter nameservers in Ubuntu to see if that helps.

Thank you for your answer, but I already did that and I see no difference here.
I read about some files in /etc where settings are stored but I don't know exactly which files and what should be stored in them.
Can you help me with this?
TIA

---

### Post by SeijiSensei on 2010-12-04
> **DeMus said:**
> Thank you for your answer, but I already did that and I see no difference here.
I read about some files in /etc where settings are stored but I don't know exactly which files and what should be stored in them.
Can you help me with this?
TIA

/etc/resolv.conf provides the nameserver configuration for your machine.  Usually this file is written by the DHCP client program, using the name server addresses provided by the DHCP server, which is typically your router.  See if the "nameserver" entries in this file are the ones you want to be using.

---

### Post by DeMus on 2010-12-05
> **SeijiSensei said:**
> /etc/resolv.conf provides the nameserver configuration for your machine.  Usually this file is written by the DHCP client program, using the name server addresses provided by the DHCP server, which is typically your router.  See if the "nameserver" entries in this file are the ones you want to be using.

Thank you for answering. I will take a look into that file. Do you happen to have an example file so I can see what should be in it? Maybe it helps me. Thanks

---

### Post by SeijiSensei on 2010-12-05
domain example.com
search example.com
nameserver 192.168.1.1
nameserver 192.168.1.100
nameserver 4.4.4.4

The first two tell the resolver to hang ".example.com" onto the end of any "unqualified" hostname like "mypc".  The last three give the nameserver addresses.  It tries them in order until it finds one that responds.  The last address is one of Google's public nameservers.

---

