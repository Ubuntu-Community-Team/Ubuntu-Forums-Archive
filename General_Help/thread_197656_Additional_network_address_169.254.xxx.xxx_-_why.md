---
title: "Additional network address 169.254.xxx.xxx - why?"
date: 2006-06-16
forum: General Help
---

### Post by tgrzejsz on 2006-06-16
Hi,
I have a question about additional addresses that for some time now are getting assigned to my eth interfaces. These addresses are for network 169.254.0.0/16. That don't cause much damage, but are sometimes a little annoying:
-I can no longer just write:
    ifconfig
 To see my network address, I have to write:
    ip addr show eth1
-KDE (or Kubuntu) network configuration is not prepared for this, as it only shows one address for an interface. I think that with GNOME it is better.
-When using nmblookup, samba gets confused by a network mask of the first address assigned to an interfaces. So when I have the following addresses assigned to eth2:
169.254.41.17/16
192.168.1.1/24
nmblookup sends broadcasts to:
169.254.255.255 and...
192.168.255.255
instead of 192.168.1.255

So what is the purpose of assigning these addresses?

Greetings,
Tomek

---

### Post by tgrzejsz on 2006-06-16
After reading some wikipedia I can see that this can be related to zeroconf running on my computer. But knowing this doesn't help described minor issues.

Tomek

---

### Post by george2+ on 2006-06-16
Internet Assigned Numbers Authority (IANA) has reserved private IP addresses in the range of 169.254.0.0 -169.254.255.255 for Automatic Private IP Addressing.

In my experience this is what your NIC gives you when it can't see the DHCP server. My problem used to be not plugging the cable in, yours is more subtle and I can't help further than this, sorry.

John

---

