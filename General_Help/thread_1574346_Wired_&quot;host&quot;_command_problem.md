---
title: "Wired &quot;host&quot; command problem"
date: 2010-09-14
forum: General Help
---

### Post by speedfirst on 2010-09-14
my "host" command seems never lookup /etc/hosts file. My hostname is "myubuntu", and the /etc/hosts has this line:

```
127.0.1.1   myubuntu
```

and /etc/host.conf are

```
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
```

/etc/nsswitch.conf contains
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

```

However, when I type "host myubuntu", the result is:
```
Host myubuntu not found: 3(NXDOMAIN)
```

What's more wired is ping can lookup the correct IP:

```
$ ping myubuntu
PING myubuntu (127.0.1.1) 56(84) bytes of data.
64 bytes from myubuntu (127.0.1.1): icmp_seq=1 ttl=64 time=0.044 ms
64 bytes from myubuntu (127.0.1.1): icmp_seq=2 ttl=64 time=0.025 ms
64 bytes from myubuntu (127.0.1.1): icmp_seq=3 ttl=64 time=0.026 ms
...

```

I find a possible reason is that apt-get installed bind9-host as default. But I'm not sure.

My Ubuntu version is 10.04.

Could anyone give a hand? Many thanks.

---

