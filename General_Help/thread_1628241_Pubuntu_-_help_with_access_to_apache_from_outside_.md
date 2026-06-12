---
title: "Pubuntu - help with access to apache from outside pubuntu using slirp"
date: 2010-11-22
forum: General Help
---

### Post by greavette on 2010-11-22
Hello,

For those who don't know (and might be interested), pubuntu is a portable version of ubuntu that runs using colinux.  Can be run from a USB stick too.  I'm just playing with it and for those that may have done some configuration to it, I'm hoping you can help me.

I've installed a lamp server on my pubuntu and would like to access it from outside pubuntu (host and other PC's on my internal network).

I've followed the instructions from this page:
[http://ubuntuforums.org/showthread.php?p=7081741](http://ubuntuforums.org/showthread.php?p=7081741)

I've updated my portable_ubuntu.conf file and added this line:
```
eth1=slirp,00:ff:75:39:D3:C1,tcp:22:22/tcp:80:80
```

my  networking section of the conf file looks like this:
```
network_mode=slirp
#ports_to_redirect=protocol(udp,tcp):Windows_port:Portable_Ubuntu_port/protcol(udp,tcp):other_Windows_port:other_Portable_Ubuntu_port
#ports_to_redirect=tcp:22:22
eth1=slirp,00:ff:75:39:D3:C1,tcp:22:22/tcp:80:80
```

I then restarted pubuntu.  I checked my network interfaces and they now look like this:
```
eth0      Link encap:Ethernet  HWaddr 00:ff:75:39:d3:c1  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12185149 (12.1 MB)  TX bytes:78147910 (78.1 MB)
          Interrupt:10 

eth1_rename Link encap:Ethernet  HWaddr 00:ff:75:39:d3:c1  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1344 (1.3 KB)  TX bytes:3656 (3.6 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2612 (2.6 KB)  TX bytes:2612 (2.6 KB)

```

I've confirmed that my networking still works from inside pubuntu and I can access my webserver from inside pubuntu, but when I try accessing my webserver from my host pc (outside pubuntu) I get a page not found error.

What am I missing? 

Thanks,

Charles.

---

