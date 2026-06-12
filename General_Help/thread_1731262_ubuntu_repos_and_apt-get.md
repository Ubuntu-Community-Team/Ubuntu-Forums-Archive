---
title: "ubuntu repos and apt-get"
date: 2011-04-16
forum: General Help
---

### Post by intervade on 2011-04-16
Alright, I've been going at this for hours. My problem starts with trying to run "apt-get update", I get a long hang time for some reason. It hangs at Waiting For Headers, but there is more going on I believe so I decided to run "strace apt-get update" to find out what is going on. 

Now, this was my attempt at Canadian repos. After waiting for about 2 minutes on the strace I get a list of the following... 

```
write(2, "Failed to fetch http://ca.archiv"..., 183Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  Unable to connect to ca.archive.ubuntu.com:http: [IP: 91.189.92.170 80]
) = 183
```I get this a lot, and its not just the canadian repos, I've tried US, UK and Great Britain. So, I decided to actually attempt to download this file, [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz) .. good news is on my desktop (windows 7) I can download this file no problem but.. when I wget get this file from the linux machine, it can't resolve the host. 

This seems to be a network configuration problem but, I'm not positive. I have 2 different network cards that I've tried and I've also tried a different ethernet cables with no luck.. I'm not sure why I can't download or connect to these repos on the linux machine itself. I don't think its my router because I can connect to these repos on my windows machine. 

Any help on this would be greatly appreciated!

---

### Post by Bucky Ball on 2011-04-16
Tried:

```
sudo apt-get update
```

?

---

### Post by intervade on 2011-04-17
Yes, my apologies. All of the commands were ran under sudo.

---

### Post by skynet2060 on 2011-04-17
you are probably using your loopback address.

In your terminal type:

# **ifconfig**

and see if your etho, eth1 cards are being used and have the correct Ip address from your router's dhcp service.

---

### Post by intervade on 2011-04-17
Well, here is what it returned.. my ip address is correct, I think. I have no knowledge of networking really. I can ping websites, but I can't wget them, no idea why. 

```
eth0      Link encap:Ethernet  HWaddr 00:04:e2:0c:1b:60
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:e2ff:fe0c:1b60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000
          RX bytes:18275 (18.2 KB)  TX bytes:19603 (19.6 KB)
          Interrupt:18 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:37137 (37.1 KB)  TX bytes:37137 (37.1 KB)

```

---

