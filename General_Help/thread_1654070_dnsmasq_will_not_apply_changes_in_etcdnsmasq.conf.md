---
title: "dnsmasq will not apply changes in /etc/dnsmasq.conf"
date: 2010-12-27
forum: General Help
---

### Post by phatypus on 2010-12-27
Hello,

ubuntu: 10.04
dnsmasq: 2.52-1ubuntu0.1

I've installed dnsmasq and it is performing DNS duties correctly.  I'd like to limit access to the dnsmasq service to a specific address or interface.  I've tried adding variations and combinations of the following to /etc/dnsmasq.conf:

```
interface=eth0
```
and 
```
listen-address=1.2.3.4
```

... but after I restart dnsmasq, it's still listening on all interfaces/IP addresses:

```
$ netstat -an | grep 53
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
udp        0      0 0.0.0.0:53              0.0.0.0:*                          
udp6       0      0 :::53                   :::*
``` 

I've read the dnsmasq man page and I think I'm making the correct changes, but it seems that any changes I make to /etc/dnsmasq.conf are not being applied when the service starts.  Obviously this isn't ideal, so can anyone advise how to configure dnsmasq?

TIA

---

### Post by dcstar on 2010-12-27
> **phatypus said:**
> Hello,

ubuntu: 10.04
dnsmasq: 2.52-1ubuntu0.1

I've installed dnsmasq and it is performing DNS duties correctly.  I'd like to limit access to the dnsmasq service to a specific address or interface.  I've tried adding variations and combinations of the following to /etc/dnsmasq.conf:

```
interface=eth0
```
and 
```
listen-address=1.2.3.4
```

... **but after I restart dnsmasq**, it's still listening on all interfaces/IP addresses:
........
**How?:**
```
       When  it  receives a SIGHUP, dnsmasq clears its cache and then re-loads
       /etc/hosts and /etc/ethers and  any  file  given  by  --dhcp-hostsfile,
       --dhcp-optsfile  or  --addn-hosts.   The  dhcp  lease  change script is
       called for all existing DHCP leases. If --no-poll is  set  SIGHUP  also
       re-reads  /etc/resolv.conf.   [B]SIGHUP does NOT re-read the configuration
       file.[/B]
```

---

