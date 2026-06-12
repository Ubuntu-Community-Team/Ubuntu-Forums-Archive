---
title: "Can't ping or SFTP to my hostname"
date: 2009-06-25
forum: General Help
---

### Post by davescafe on 2009-06-25
I am running Ubuntu 9.04 on my desktop. At some point in the last month or so, I have lost the ability to connect to this desktop via SFTP from other machines. In attempting to debug the problem, I have found that I can't ping my hostname either.

Using the name 88088 for my hostname, here are some symptoms:

In a terminal window:
[INDENT]ping 88088
Result: ping: unknown host 88088[/INDENT]

[INDENT]hostname
Result: 88088[/INDENT]

[INDENT]hostname -f
Result: hostname: Unknown host[/INDENT]

in Nautilus:
[INDENT]sftp://88088/
Result: Could not display "sftp://88088", because the host could not be found[/INDENT]

Contents of /etc/hostname:
[INDENT]88088[/INDENT]

Contents of /etc/hosts
[INDENT]
127.0.0.1	88088	localhost.localdomain	localhost
127.0.1.1	88088.davesorg.davesdomain

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/INDENT]

I have tried various changes with the hosts file, but nothing seems to work. Can anybody help?

---

### Post by pennacook on 2009-06-25
You might need to set up another interface for your '88088". or put the 88088 at the end of the first localhost line. 

From the man page the line needs to be:

```
IP_address canonical_hostname aliases
```

Can you even ping localhost in a term window?

What does ifconfig -a show?

---

### Post by davescafe on 2009-06-25
> **pennacook said:**
> You might need to set up another interface for your '88088". or put the 88088 at the end of the first localhost line. 

From the man page the line needs to be:

```
IP_address canonical_hostname aliases
```

Can you even ping localhost in a term window?

What does ifconfig -a show?

I can successfully "ping localhost":
[INDENT]username@88088:~$ ping localhost
PING 88088 (127.0.0.1) 56(84) bytes of data.
64 bytes from 88088 (127.0.0.1): icmp_seq=1 ttl=64 time=0.060 ms
64 bytes from 88088 (127.0.0.1): icmp_seq=2 ttl=64 time=0.068 ms
64 bytes from 88088 (127.0.0.1): icmp_seq=3 ttl=64 time=0.073 ms[/INDENT]

ifconfig-a produces the following results: 
[INDENT]username@88088:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          inet addr:10.45.xx.xx  Bcast:10.45.xx.xx  Mask:255.255.254.0
          inet6 addr: fe80::xxx:xxx:xxx:xxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46289280 (46.2 MB)  TX bytes:9481918 (9.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17873 (17.8 KB)  TX bytes:17873 (17.8 KB)

pan0      Link encap:Ethernet  HWaddr 76:xx:xx:xx:xx:xx  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/INDENT]

My /etc/hosts file as I have it now (and as I listed it in my previous post) is the hosts file that was automatically crated by Ubuntu 9.04. What's a bit odd is that I installed 9.04 on two machines simultaneously, and I have tried to configure both machines identically. Despite having the same programs installed and the same configuration, the automatically-created hosts file on the other machine is a bit different. This other machine works as expected, and can successfully ping to it's own host name and SFTP works. The other machine is named 88088-l and it's hosts file looks like this:

[INDENT]127.0.0.1	localhost
127.0.1.1	88088-l

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/INDENT]

I have tried setting up the hosts file of the defective machine (88088) to mimic the settings in the working machine (88088-l), but I did not see a change in the defective machine. Further, I have added entries to the defective machine's hosts file like this:

[INDENT]127.0.1.1 88088.davesorg.davesdomain 88088[/INDENT]

This does not work. However, when I set up an alias like this:

[INDENT]74.125.19.103  [www.google.com](www.google.com) google[/INDENT]

It works as expected (I can type "ping google" and ping correctly finds the alias).

It's a mystery to me. If you can provide any insight, I would much appreciate it.

---

