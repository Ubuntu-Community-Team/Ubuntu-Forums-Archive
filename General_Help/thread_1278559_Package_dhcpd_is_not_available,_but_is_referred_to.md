---
title: "Package dhcpd is not available, but is referred to by another package etc etc"
date: 2009-09-29
forum: General Help
---

### Post by t0p on 2009-09-29
I want to follow [this guide]("https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing").  It tells me to install dhcpd.  But it seems I can't - this is the output I get when I try:

```
t0p@machine:~$ sudo apt-get install dhcpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dhcpd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dhcpd has no installation candidate
t0p@machine:~$ 

```

From looking in Synaptic, I found that there are a few packages that are *similar* to dhcpd: eg udhcpd, dhcp3-server, dhcp3-server-ldap.

Is it possible for me to install dhcpd from somewhere?  If not, which other package would be suitable?

---

### Post by mattkoehn on 2009-09-29
dhcp3-server is what you want.

---

### Post by Iowan on 2009-09-29
> **t0p said:**
>  If not, which other package would be suitable?So far, I'm fond of **dnsmasq**.

---

### Post by t0p on 2009-09-29
> **mattkoehn said:**
> dhcp3-server is what you want.

Thanks.

---

