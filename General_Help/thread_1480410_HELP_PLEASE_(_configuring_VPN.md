---
title: "HELP PLEASE :( configuring VPN"
date: 2010-05-11
forum: General Help
---

### Post by helpppp on 2010-05-11
I've established a connection to my VPN through KVpnc, but now that im connected, it still says that my ip is the same, and there is no change in my browser's activity. How do I get my ethernet to go through the VPN connection!? any help with this matter is would be greatly appreciated :(

---

### Post by cdenley on 2010-05-11
> **helpppp said:**
> I've established a connection to my VPN through KVpnc, but now that im connected, it still says that my ip is the same, and there is no change in my browser's activity. How do I get my ethernet to go through the VPN connection!? any help with this matter is would be greatly appreciated :(

I'm not familiar with KVpnc, but a VPN isn't supposed to change your existing network interface. It creates a new virtual interface. What I think you want is to use your VPN interface for the default route.
```

ifconfig
route -n

```

---

### Post by helpppp on 2010-05-11
ok I see the ips O.O.... and my network devices O.O.... now what :( how do I set the default route????

---

### Post by cdenley on 2010-05-11
A little hard for me to give you the commands you need to run if you don't provide the output from the commands I posted.

---

### Post by helpppp on 2010-05-11
its cluttering up when I post it >< what am I suppose to route where?

---

### Post by cdenley on 2010-05-11
Use "code" tags to post output.
[NOPARSE]
```

my output here

```
[/NOPARSE]

Either provide the requested output, or learn how to use the route command.
```

man route

```

---

### Post by Zorael on 2010-05-11
KVpnc has a setting that makes it set your default route to be via the VPN upon establishing the connection. Dig through the configuration dialogs and enable it there.

I can't give precise pointers and list names of settings without disconnecting KVpnc myself first.

---

### Post by helpppp on 2010-05-11
.

---

### Post by helpppp on 2010-05-11
```
  eth0      Link encap:Ethernet  HWaddr --:--:--:--:--:--           inet addr:--.--.86.199  Bcast:255.255.255.255  Mask:255.255.254.0           UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1           RX packets:12652 errors:0 dropped:0 overruns:0 frame:0           TX packets:11365 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000           RX bytes:4876186 (4.8 MB)  TX bytes:1274084 (1.2 MB)           Interrupt:16  lo        Link encap:Local Loopback           inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:78 errors:0 dropped:0 overruns:0 frame:0           TX packets:78 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0           RX bytes:3900 (3.9 KB)  TX bytes:3900 (3.9 KB)  ppp0      Link encap:Point-to-Point Protocol           inet addr:--.--.186.35  P-t-P:--.--.186.2  Mask:255.255.255.255           UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1           RX packets:781 errors:0 dropped:0 overruns:0 frame:0           TX packets:6 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:3           RX bytes:48369 (48.3 KB)  TX bytes:130 (130.0 B)   Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Iface --.--.186.2    --.--.86.1      255.255.255.255 UGH   0      0        0 eth0 --.--.186.2    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0 --.--.86.0     0.0.0.0         255.255.254.0   U     0      0        0 eth0 0.0.0.0         --.--.86.1     0.0.0.0         UG    0      0        0 eth0  
```  thx in advance :)  also this is the outputput from Kvpnc if it helps ```
 info: Saving profiles and global options... info: Profile "---" saved. info: Profile "---" saved. info: Profile "---" saved. info: Profiles saved. info: Global options saved. debug: No default interface given, tried default interface, got success, using "eth0". debug: Username: i--- debug: Trying to connect to server "---" with user "---"...  debug: [pppd] Using interface ppp0 debug: [pppd] Connect: ppp0 /dev/pts/1 debug: [pppd] CHAP authentication succeeded debug: [pppd] MPPE 128-bit stateless compression enabled debug: [pppd] replacing old default route to eth0 [--.--.86.1] debug: [pppd] Cannot determine ethernet address for proxy ARP debug: [pppd] local IP address --.--.186.35 debug: [pppd] remote IP address --.--.186.2 success: Successful connected to server "---" user: "---" at Tue May 11 12:28:39 2010 [PPTP] success: Connection established.
```  [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by cdenley on 2010-05-12
```

sudo route del default
sudo route add default gw --.--.186.2

```

You should be able to configure kvpnc to do this automatically, but I'm not familiar with it.

---

### Post by helpppp on 2010-05-12
didnt work :S internet pages wont load

---

### Post by cdenley on 2010-05-12
> **helpppp said:**
> didnt work :S internet pages wont load

Are you using DNS servers which can be accessed through your VPN?
```

nc -z -v -w 5 91.189.94.156 80
dig @8.8.8.8 ubuntu.com

```
Did you verify that your default route gateway matches the current IP of your VPN server?

---

### Post by Zorael on 2010-05-13
See screenshot for where you can set KVpnc to set your vpn connection as its default route.

You may need to manually enter the DNS your connection is to use. I found that it fails to autodetect it for me, even though it should supposedly be able to retrieve it from the vpn server.

---

