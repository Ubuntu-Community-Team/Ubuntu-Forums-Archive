---
title: "ifconfig is missing tap device"
date: 2010-02-03
forum: General Help
---

### Post by linux000019 on 2010-02-03
im trying to run openvpn from the root command prompt and heres the problem:

linux-k1bg:/etc/openvpn # openvpn client.ovpn 
Wed Feb  3 15:07:50 2010 OpenVPN 2.1.1 i686-pc-linux-gnu [SSL] [EPOLL] built on Feb  3 2010
Wed Feb  3 15:07:50 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables                                                                                                 
Wed Feb  3 15:07:50 2010 WARNING: file 'static.key' is group or others accessible                               
Wed Feb  3 15:07:50 2010 TUN/TAP device tap0 opened                                                             
SIOCADDRT: No such process                                                                                      
Wed Feb  3 15:07:50 2010 ERROR: Linux route add command failed: external program exited with error status: 7    
Wed Feb  3 15:07:50 2010 UDPv4 link local (bound): [undef]:443                                                  

linux-k1bg:/etc/openvpn # ps aux | grep openvpn
root     21209  0.0  0.0   2316   712 pts/1    R+   15:10   0:00 grep openvpn
linux-k1bg:/etc/openvpn # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:90:CA:82
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13828 (13.5 Kb)  TX bytes:13828 (13.5 Kb)

wlan0     Link encap:Ethernet  HWaddr 00:1F:3C:B5:C9:66
          inet addr:192.168.0.81  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:feb5:c966/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41622339 (39.6 Mb)  TX bytes:3836818 (3.6 Mb)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-B5-C9-66-62-35-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

linux-k1bg:/etc/openvpn # brctl show
bridge name     bridge id               STP enabled     interfaces
linux-k1bg:/etc/openvpn #

---

### Post by bodhi.zazen on 2010-02-03
Not sure what you are doing exactly, I can not tell from that wall of text =)

Did you configure a bridge ? I do not see it.

Also, are you trying to bridge a wireless card ? I do not think you can do that.

See : [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by linux000019 on 2010-02-03
no im just trying to connect through openvpn. linux doesn't recognize that there should be a device connected to the network on the other end and is unable to redirect the gateway.

it works like a charm in windows and if my display driver wasn't a piece of **** i'd be using vista right now; as it is though the black screen of death keeps me from it.

---

### Post by gmargo on 2010-02-04
> **linux000019 said:**
>  
Wed Feb  3 15:07:50 2010 OpenVPN 2.1.1 i686-pc-linux-gnu [SSL] [EPOLL] **built on Feb  3 2010**


Why are you compiling your own openvpn?  What does the one in the repository do?

---

