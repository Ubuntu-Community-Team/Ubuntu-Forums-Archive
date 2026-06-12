---
title: "Simplest possible dhcp failover not working"
date: 2011-10-07
forum: General Help
---

### Post by suprstar on 2011-10-07
Ubuntu 10.04 LTS dhcp3-server - I've stripped the config down to 1 subnet with next to no options. The primary/secondary see each other start and stop, they balance the pool, but when the primary load balances a request to the secondary, the secondary acts like it doesn't even hear the request. Not a single line in syslog. The primary's syslog looks like this:


Oct 7 09:15:01 svc1 dhcpd: DHCPDISCOVER from 00:1f:fb:22:8a:55 via 199.91.247.254: load balance to peer dhcp
Oct 7 09:15:02 svc1 dhcpd: DHCPDISCOVER from 00:1f:fb:22:8c:a8 via 199.91.247.254: load balance to peer dhcp
Oct 7 09:15:05 svc1 dhcpd: DHCPDISCOVER from 00:1f:fb:22:8c:a8 via 199.91.247.254: load balance to peer dhcp
Oct 7 09:15:09 svc1 dhcpd: DHCPDISCOVER from 00:26:82:67:14:6c via 199.91.247.254: load balance to peer dhcp

Couldn't be any simpler, I've been beating my head for hours, what am I missing here??  On either server, if I run

tcpdump host 10.250.0.9 port 520

I get nothing, even when .8 is supposedly offloading one of these requests.  If I similarly watch the primary, I see lots of .9 talking to .8, and .8 responding.

Primary
----------------
```

ddns-update-style none;
authoritative;
log-facility local7;

option domain-name-servers 208.74.224.4, 208.74.224.5;
default-lease-time 86400;
max-lease-time 86400;


failover peer "dhcp" {
    primary;
    address 10.250.0.8;
    port 519;
    peer address 10.250.0.9;
    peer port 520;
    max-response-delay 60;
    max-unacked-updates 10;
    mclt 3600;
    split 128;
    load balance max seconds 3;
}

# This is just here to the server knows
# which interface to listen on:
subnet 10.250.0.0 netmask 255.255.255.192 {}

# This is the actual subnet I'm trying to serve:
subnet 199.91.244.0 netmask 255.255.252.0  {
    option subnet-mask 255.255.252.0;
    option routers 199.91.244.1;
    pool {
        failover peer "dhcp";
        range 199.91.244.11 199.91.247.199;
    }
}

```

Secondary:
----------------
```

ddns-update-style none;
authoritative;
log-facility local7;

option domain-name-servers 208.74.224.4, 208.74.224.5;
default-lease-time 86400;
max-lease-time 86400;

failover peer "dhcp" {
    secondary;
    address 10.250.0.9;
    port 520;
    peer address 10.250.0.8;
    peer port 519;
    max-response-delay 60;
    max-unacked-updates 10;
}

subnet 10.250.0.0 netmask 255.255.255.192 {}

subnet 199.91.244.0 netmask 255.255.252.0  {
    option subnet-mask 255.255.252.0;
    option routers 199.91.244.1;
    pool {
        failover peer "dhcp";
        range 199.91.244.11 199.91.247.199;
    }
}

```

---

