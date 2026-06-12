---
title: "Wireless network works fine using Network Manager but does not work when using Bash-&gt;"
date: 2009-10-16
forum: General Help
---

### Post by peterswinkels on 2009-10-16
Hello,

I'm trying to connect to my wireless network using the Bash shell. Although I can connect to my wireless networks fine using the Network Manager in GNOME, I keep getting an IPV4LL address when trying to connect using commands in Bash. Using the -L (avoids IPV4LL addresses) switch with the dhcpcd command doesn't work. I can detect my wireless using the "iwlist scanning" command though.

Commands used while attempting to connect using Bash:
```

peterswinkels@petelp2:~$ sudo ifconfig eth1 down
peterswinkels@petelp2:~$ sudo ifconfig eth1 up
peterswinkels@petelp2:~$ sudo iwconfig eth1 essid "myaccesspoint"
peterswinkels@petelp2:~$ sudo iwconfig eth1 key s:mykey
peterswinkels@petelp2:~$ sudo dhcpcd eth1
err, eth1: timed out
warn, eth1: using IPV4LL address 169.254.139.173
dhcpcd.sh: interface eth1 has been configured with new IP=169.254.139.173
peterswinkels@petelp2:~$ 

```

dmesg:
```

[   36.308088] eth1: no IPv6 routers present
[  599.377358] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  642.984984] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  653.364176] eth1: no IPv6 routers present
[  757.442284] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  810.802443] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  863.854746] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

lspci:
```

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

Websites found while searching for information:
[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)
[http://www.linuxforums.org/forum/ubuntu-help/126364-how-connect-wireless-network-ubuntu.html](http://www.linuxforums.org/forum/ubuntu-help/126364-how-connect-wireless-network-ubuntu.html)

My computer is a Dell Inspiron 6000 running Ubuntu 9.04 - See above information for details on the network cards.

Thanks in advance.

---

