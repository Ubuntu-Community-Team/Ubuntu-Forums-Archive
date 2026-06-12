---
title: "Updating  interfaces file in effort to fix apt-get"
date: 2011-06-20
forum: General Help
---

### Post by justineamelie on 2011-06-20
I've been trying to fix a problem with apt-get update for a couple of days now with no luck. Here's the output:

```
Ign http://security.ubuntu.com natty-security InRelease
Err http://security.ubuntu.com natty-security Release.gpg
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Ign http://security.ubuntu.com natty-security Release
Ign http://security.ubuntu.com natty-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Err http://us.archive.ubuntu.com natty Release.gpg
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-security Release.gpg
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates Release.gpg
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Ign http://us.archive.ubuntu.com natty Release
Ign http://us.archive.ubuntu.com natty-security Release
Ign http://us.archive.ubuntu.com natty-updates Release
Ign http://us.archive.ubuntu.com natty/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/multiverse i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Err http://security.ubuntu.com natty-security/universe i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/main i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted Sources/DiffIndex
Err http://security.ubuntu.com natty-security/multiverse i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/restricted i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/main Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/main Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/multiverse Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/multiverse Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/restricted Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/restricted Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/universe Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://security.ubuntu.com natty-security/universe Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Ign http://us.archive.ubuntu.com natty-updates/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Err http://us.archive.ubuntu.com natty-security/universe Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-security/main Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-security/multiverse Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-security/restricted Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/main Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/universe Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/restricted Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/multiverse Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/main i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/universe i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/restricted i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/multiverse i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/main Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/main Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/multiverse Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/multiverse Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/restricted Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/restricted Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/universe Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty/universe Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/universe Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/main Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/multiverse Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/restricted Sources
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/universe i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/main i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/main Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/main Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/restricted Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
Err http://us.archive.ubuntu.com natty-updates/universe Translation-en
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22: Invalid argument)
```

The problem seems to be very much the same as what's described here: [http://ubuntuforums.org/showthread.php?t=1691491&highlight=odd+problems+with+apt-get](http://ubuntuforums.org/showthread.php?t=1691491&highlight=odd+problems+with+apt-get)

According to that thread, the fix is to add the gateway IP to /etc/network/interfaces

The problem I'm having is that I don't know exactly what to do to the file in my situation. I've been googling around but any reference to the gateway IP seems to be as part of setting up eth0 (or whathaveyou) for a static IP address. I'm not trying to use a static IP -- I'd just like to add the gateway to the interfaces file I have now. I must admit that I'm not network savvy enough to know whether what I'm saying is logical (perhaps a static IP and an explicitly defined gateway IP are mutually inclusive things?). 

No matter. I'd really just like top know what I should do if with my interfaces file in an effort to fix apt-get update. That file currently looks like this:

```
auto lo
iface lo inet loopback
```

Thank you,
~Justine

---

### Post by ultraata on 2011-06-21
Please post following outputs:
ifconfig 
ifconfig -a
netstat -nr
cat /etc/resolv.conf

---

### Post by justineamelie on 2011-06-21
ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:08:74:94:20:ad  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe94:20ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13828 errors:0 dropped:0 overruns:1 frame:0
          TX packets:10658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11123710 (11.1 MB)  TX bytes:1676951 (1.6 MB)
          Interrupt:11 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr 00:08:74:94:20:ad  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe94:20ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13831 errors:0 dropped:0 overruns:1 frame:0
          TX packets:10658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11123986 (11.1 MB)  TX bytes:1676951 (1.6 MB)
          Interrupt:11 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:bb:b1:36  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x8000 Memory:f8ffe000-f8ffefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

netstat -nr:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

resolv.conf:

```

# Generated by NetworkManager
nameserver 192.168.1.1

```

---

### Post by gmargo on 2011-06-21
> **justineamelie said:**
> 
```

  Cannot initiate the connection to [COLOR=Red]3128:80[/COLOR] (0.0.12.56). - connect (22: Invalid argument)

```

I suspect that you have attempted to configure the apt system to go through a proxy (perhaps **squid**?), but have configured it incorrectly.
Do you have anything in /etc/apt/apt.conf or /etc/apt/apt.conf.d/ related to a proxy?

---

### Post by justineamelie on 2011-06-21
I remember now... apt.conf didn't exist so I had created one and tried editing it manually. I just deleted it and apt-get is working again! I've been working so much on this computer I forgot what I have and haven't done.

Well, thank you both for your time!

---

### Post by kes333 on 2012-07-26
Thanks for the hint. In my case, /etc/apt/apt.conf was there already (created at the time of installing apt-get) with an entry:
Acquire::http::Proxy "<my.proxy.server:port>"

Moving the file away from this location made `apt-get update` work. 
I wonder why apt-get was not able to read the proxy server name from apt.conf. It had the right server name...
Thanks anyway.

---

