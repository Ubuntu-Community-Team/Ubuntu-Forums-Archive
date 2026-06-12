---
title: "Internet dowsn't working except Skype"
date: 2012-07-03
forum: General Help
---

### Post by theZiki on 2012-07-03
Hi, I have a strange problem, I can connect to any wireless network or wired but Internet connection doesn't working except Skype, other protocols seems to be blocked or what? Localhost works normally (Apache). 

Thanks.

---

### Post by matt_symes on 2012-07-03
Hi

Do you have a firewall enabled ?

Open a terminal and type

```
sudo iptables -F
```

Can you connect to the internet then ?

Are you going through a proxy ?

From the same terminal, type these command and post the output back here.

```
ping -c3 8.8.8.8
```

```
nslookup www.bbc.co.uk 8.8.8.8
```

```
cd && wget www.google.com
```

Kind regards

---

### Post by hunter.allen on 2012-07-03
Are you running some form of proxy server? If so, this could be the origin of the problem. Other than that, I don't see what you mean by it "doesn't work". 

The internet certainly isn't the problem. It is odd that you can only use skype, which leads me to think it's some kind of proxy. 

I'll need some more info. Try some terminal commands: 

```
ping -c 5 www.google.com
``` 
Post the output

```
sudo apt-get update
```

If you still have problems, connect to Ethernet and check the hardware drivers. Could be some weird proprietary package thing.

__________________________________________________________________________________________________________________________________________

Edit: Sorry matt... We posted at the same time... It's good we agree I guess!

---

### Post by theZiki on 2012-07-03
Here is output
```

ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=53 time=125 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=53 time=148 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=53 time=69.4 ms

```

```
nslookup www.bbc.co.uk 8.8.8.8
Server:                8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
www.bbc.co.uk        canonical name = www.bbc.net.uk.
Name:        www.bbc.net.uk
Address: 212.58.244.68
```

```
cd && wget www.google.com
--2012-07-03 16:37:05--  http://www.google.com/
Resolving www.google.com (www.google.com)... failed: Name or service not known.
wget: unable to resolve host address `www.google.com'
```

I cannot have update because it is same am I connected on wireless or wired connection, any internet protocol except Skype not passing, that is my conclusion.

What to do?

---

### Post by hunter.allen on 2012-07-03
Are you running through a proxy? That is important information. Please check your proxy settings.

---

### Post by theZiki on 2012-07-03
No, I'm not using any proxy.

---

### Post by hunter.allen on 2012-07-03
Would you post your /etc/network/interfaces file?

```
gedit /etc/network/interfaces
```

You could have some sort of configuration problem. This error is certainly confusing...

---

### Post by theZiki on 2012-07-03
```
auto lo
iface lo inet loopback
```

---

### Post by hunter.allen on 2012-07-03
Well there's your trouble! You don't have anything but a local loop. You aren't working with your network at all! Let's set up your config, shall we? 

```
iwconfig
```

You should have a wireless device. 

```
ifconfig
```

You should have an ethernet interface (likely eth0). 

Please post the output of these.

---

### Post by theZiki on 2012-07-03
```
 iwconfig 
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:195  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
```

```
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:25:b3:7b:a2:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:70:ca:a5  
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe70:caa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3663 errors:0 dropped:0 overruns:0 frame:763
          TX packets:3647 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:399164 (399.1 KB)  TX bytes:427632 (427.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1336809 (1.3 MB)  TX bytes:1336809 (1.3 MB)
```

---

### Post by hunter.allen on 2012-07-03
Ok. Try this out: 


```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp 

auto eth1
iface eth1 inet dhcp
```

You'll need to edit it with sudo, then just copy paste the above.

```
sudo gedit /etc/network/interfaces
```

Once you've done that, you should be able to use your network. Do the following: 

```
sudo /etc/init.d/networking restart
```

This should reset your network configuration. Try to use it. Hope it works!

---

### Post by theZiki on 2012-07-03
I did that and this is the result:

```

...
resolvconf: Error: /etc/resolv.conf isn't a symlink, not doing anything.

```

And now nothing is working, and I don't even see my networks.

---

### Post by hunter.allen on 2012-07-03
This is found in a bug report here: [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/922677](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/922677)

Since it isn't working now, just undo what I told you... It'll clear that up. 

I'd say it's time to bring out the install disc. This is very bizarre. Anyone else have some input?

---

### Post by matt_symes on 2012-07-03
Hi

Let's try to fix this before contemplating a reinstall.

First please change /etc/network/interfaces back to what is was. It should just contain the text below.
[FONT=monospace]
[/FONT]```
auto lo 
iface lo inet loopback 
```If you want Network Manager to control those interfaces then you do not need the eth0 entries in the interfaces file.

Looking at the output you posted from previous posts, you have internet connectivity as ping works. 

Your dns resolver is working when you use googles names servers, that is good.

wget is failing when it tries to resolve the url to an IP address.

You have a problem with resolvconf by the looks of it.

Please post the output of these commands (from a terminal).

```
ls -l /etc/resolv.conf
```That is a small L after ls.

```
cat /etc/resolv.conf
``````
ps aux | grep -i dns
```Kind regards

---

### Post by Wim Sturkenboom on 2012-07-20
// Edit

I apologize; this thread was a bit older than I initially thought so my comments were not valid.

---

