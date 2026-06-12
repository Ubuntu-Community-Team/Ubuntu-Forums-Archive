---
title: "Server not found :Ubuntu 9.10"
date: 2009-12-25
forum: General Help
---

### Post by mohitkhannanu on 2009-12-25
I am a complete newbie and also an average computer user. I just downloaded 
Ubuntu 9.10. I have MTNL Broadband connection(Modem:Huawei SmartAX MT882).
Initially in network manager dynamic(dhcp)option was selected and i was getting something like wired connection inactive/disconnected.
then i chose static and entered ipv4 settings, the same one which i use in windows xp sp2. this made wired Auto eth0 active
then i opened mozilla and tried to open google and other websites but got server not found.
same thing happened when i used ping(tried this because this was given in help.)

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0c:76:af:77:48  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:feaf:7748/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360 (360.0 B)  TX bytes:4949 (4.9 KB)
          Interrupt:23 Base address:0xa000 
now wat to do?
explain in layman lang.

---

### Post by spiderbatdad on 2009-12-25
This looks out of place to me:
```
Interrupt:23 Base address:0xa000 
```
Are you running some program to block ip addresses? Firewall or dan's guardian?
Or the modem software isnt properly installed

---

### Post by mohitkhannanu on 2009-12-25
I will prefer if u will guide completely as i am a novice.
net runs fine on windows and i haven't downloaded any sw/package as  such.

---

### Post by mohitkhannanu on 2009-12-25
Is there any s/w for Modem
I dont use any on win.

---

### Post by Iowan on 2009-12-25
Are you pinging by name or IP address? Try **ping -c5 209.85.225.103**

---

### Post by mohitkhannanu on 2009-12-25
ping -c5 209.85.225.103
connect: Network is unreachable

---

### Post by Iowan on 2009-12-25
Not a good sign...
Early on, there were several threads about problems with the Huawei modems. I hope a fix got found... but I'll need to look for one.

---

### Post by mohitkhannanu on 2009-12-25
Hey, u know wat
earlier when i installed ubuntu 9.04 and linux mint 7 internet worked but then some days later i got my modem replaced. 
From then onwards net didn't work on either mint or ubuntu.

---

