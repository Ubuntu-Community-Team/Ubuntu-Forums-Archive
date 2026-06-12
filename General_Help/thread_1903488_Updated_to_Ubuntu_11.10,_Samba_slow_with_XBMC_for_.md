---
title: "Updated to Ubuntu 11.10, Samba slow with XBMC for Xbox"
date: 2012-01-02
forum: General Help
---

### Post by CheapoDepot on 2012-01-02
I had Ubuntu 10.10 working fine using samba to connect to my xbox xbmc through the network. The folder access time was great and videos played immediately with no skipping. I then updated to Ubuntu 11.04 using the update manager. I immediately updated to Ubuntu 11.10. Computer got really messed up here so I decided to install Ubuntu 11.10 from disc over my current installation.

I got everything working ok except my xbox xbmc on the network. Browsing through the folders takes 15 seconds per folder and all videos lag now. I doubt it is an xbox xbmc problem because it's been working fine for 2 years. When accessing my Ubuntu 11.10 computer through Windows XP, it works fine.

I've tried multiple setups of /etc/samba/smb.conf with no luck of improving performance. Is this a Ubuntu 11.10 problem or did I setup something incorrectly or forget to do something?

/etc/samba/smb.conf
```

[global]
workgroup = WORKGROUP
netbios name = SERVER
server string = SERVER
log file = /var/log/samba/log.%m
max log size = 50
map to guest = bad user
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
dns proxy = no

[mythtv]
path = /mythtv
public = yes
only guest = yes
writable = yes

```/etc/hosts
```

127.0.0.1    localhost
192.168.1.1    SERVER

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```/etc/hostname
```
SERVER
```testparm -s
```

yoda@SERVER:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[mythtv]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = SERVER
    map to guest = Bad User
    log file = /var/log/samba/log.%m
    max log size = 50
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = No
    dns proxy = No

[mythtv]
    path = /mythtv
    read only = No
    guest only = Yes
    guest ok = Yes

```I don't recall the IP6 in the hosts, but it's been awhile since I've looked at it the old hosts file that I used (which does not exist anymore).

Any help is much appreciated.

---

### Post by CheapoDepot on 2012-01-04
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:13:d3:0b:d7:48  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13025319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12578458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3539570040 (3.5 GB)  TX bytes:2240717406 (2.2 GB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233816 (233.8 KB)  TX bytes:233816 (233.8 KB)

```

---

### Post by CheapoDepot on 2012-01-04
Wow, I don't know how to explain why this wasn't working correctly but I'll try because I got it working.

_Solution_
Remove all sources from the xbox xbmc videos, music, and pictures menus. I removed them from the library as well when prompted. Then go to Add Source and the network should browse fine through samba. Select your source like normal and it plays smoothly.

_Cause?_
When I reinstalled Ubuntu 11.10 over the corrupt "upgraded" Ubuntu 11.10, I was not allowed to use my same Computer Name for some reason. I recall a message like "this Computer Name already exists". Hence, I selected another Computer Name, "SERVER". During my troubles, I tried changing it back through the "hosts" and "hostname" files and the xbox xbmc still did not work properly... not sure why... So, I ended up leaving everything as the new computer name "SERVER".

I knew all my "pre-upgrade" sources were pointing to the wrong location and I was trying to "edit" them in xbmc to the new sources by browsing. When doing so, I believe all of the other sources (about 10 to 15) were constantly trying to access the wrong location causing everything to slow down to snail speed.

_Conclusion_
Everything except the xbox xbmc ended up being set up correctly despite my initial thoughts. I find it strange that xbox xbmc would constantly try to connect to sources even when not being used. Perhaps that's a xbmc problem.

Note: I am using an old XBMC version on the original xbox. I do not believe that XBMC supports the original xbox anymore. Newer releases may not have any issue.

---

