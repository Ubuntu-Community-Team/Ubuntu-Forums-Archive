---
title: "Unable to change mac address"
date: 2010-09-20
forum: General Help
---

### Post by zaqz on 2010-09-20
I've tried
```

ifconfig hw <interface> ether <MAC address of old card>

```

in terminal, but it complains eth0 (the only interface in use) doesn't exist and consequently doesn't change anything. If I run ifconfig, I get

```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.xxx.xxx Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3296047 (3.2 MB)  TX bytes:440332 (440.3 KB)
          Interrupt:5 Base address:0x4000 


```
(valid addresses beneath those xxx's) and another entry for lo (probably not relevant here). 

My simple question is, what am I doing wrong here? I tried the command with the connection on and off, without any impact whatsoever. In /etc/network/interfaces, there's only
```

auto lo
iface lo inet loopback

```
and no mention of any eth devices. Is is just me, or why can't the hardware address be changed?

Running Xubuntu 10.04, updated, should anyone need that vital piece of information.

---

### Post by searchfgold6789 on 2010-09-20
```

sudo mousepad /etc/network/interfaces

```Add a line to it (don't change the existing two):
```
hwaddress ether xx:xx:xx:xx:xx:xx
``` Replace xx's with your new Address. Save, close then:
```
sudo /etc/init.d/networking restart
``` or reboot.
Source: [HowToGeek article]("http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/")
Hope this helps, and welcome to the forums! Don't forget to mark your thread as solved using the thread tools menu. Not doing that is the ubuntuforums equivalent of not flushing.

---

### Post by zaqz on 2010-09-20
> **searchfgold6789 said:**
> ```

sudo mousepad /etc/network/interfaces

```Add a line to it (don't change the existing two):
```
hwaddress ether xx:xx:xx:xx:xx:xx
``` Replace xx's with your new Address. Save, close then:
```
sudo /etc/init.d/networking restart
``` or reboot.
Source: [HowToGeek article]("http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/")

Sorry to disappoint you, but that didn't do a thing (I think I had tried that already in the past, with as little success). I added the line with the new address, saved and rebooted, but the old address persists in my network settings (looking at my connection information as well as ifconfig). And it wasn't like I forgot to gksudo when opening the file (not a rookie user whatever my question or post count).

Whether it's a firewall intruding in the proceedings or whatever entity rearing its ugly head here, I don't know.

---

