---
title: "Auto ethernet stopped working - what to do?"
date: 2011-04-22
forum: General Help
---

### Post by yossell on 2011-04-22
Today, out of the blue, my wired auto ethernet stopped working. It doesn't appear to be my machine or the hub as the connection is fine using windows on the computer.
 
I'm a bit clueless on the Networking front in Ubuntu. I've brought up the Network Connections box and checked that the Mac address is correct (and it is). I've tried it on Lubuntu and Openbox, but still no luck. The only oddity I see is that the Network Connections box says that the auto ethernet connection has never been used - which is of course not true.
 
Any help or pointers about how to make progress with would be very welcome.

---

### Post by spikoley on 2011-04-22
Try some of the following trouble shooting steps.

1.  Check the cables
2.  Check for an IP address

```
ifconfig
```

3.  Try pinging the router, a domain and IP address.
```
ping 192.168.1.1
```

Let us know what happens.

---

### Post by yossell on 2011-04-22
Thanks spikoley,
 
I double checked the cables but I think they should be ok as the internet works fine in windows.
 
Below is the output of the commands.
 
Using this, I tried to configure the ipv4 settings manually, entering teh address and netmask numbers - and made some progress in that I now get the wired connection is active. However, I still can't get on the internet - I'm guessing that there are further fields I need to fill - DNS servers? Search Domains?
 
 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:65:33:60  
          inet6 addr: fe80::224:8cff:fe65:3360/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5254 (5.2 KB)  TX bytes:3546 (3.5 KB)
          Interrupt:27 Base address:0x2000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
 
ping 192.168.1.1
connect: Network is unreachable

---

### Post by spikoley on 2011-04-22
You can use OpenDNS or Google's DNS.

[OpenDNS]("https://store.opendns.com/setup/device/ubuntu/")
208.67.222.222
208.67.220.220

[Google DNS]("http://code.google.com/speed/public-dns/docs/using.html")
8.8.8.8
8.8.4.4

It sounds like your router's DHCP server isn't providing you with an IP address.

---

### Post by yossell on 2011-04-22
Thanks,
 
I tried entering those, but while I've still got the autho ethernet active sign up, I'm still not getting onto the internet. Any other ideas gratefully received.

---

### Post by spikoley on 2011-04-22
What happens when you run ifconfig and ping something now?

---

### Post by yossell on 2011-04-22
This is what I got when I ran these again
 
[EMAIL="yossell@yossell-desktop:~$"]yossell@yossell-desktop:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:65:33:60  
          inet addr:127.0.0.1  Bcast:127.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::224:8cff:fe65:3360/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45486 (45.4 KB)  TX bytes:6378 (6.3 KB)
          Interrupt:27 Base address:0x2000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192512 (192.5 KB)  TX bytes:192512 (192.5 KB)
[EMAIL="yossell@yossell-desktop:~$"]yossell@yossell-desktop:~$[/EMAIL] ping 192.168.1.1
connect: Network is unreachable

---

### Post by dragonfly41 on 2011-04-22
I recently lost my Internet connection ..

see here    [http://ubuntuforums.org/showthread.php?t=1735427](http://ubuntuforums.org/showthread.php?t=1735427)

I'm fairly sure that this followed a major upgrade of various packages (have you gone through an upgrade recently?) and unfortunately I ended up having to reinstall .. but this time in two separate partitions "root" and "home".   Never did restore connection.

It would be useful to know how to restore Internet connection.

[P.S.]

comparing your ifconfig output with mine which follows:

          ```
inet addr:xx.xxx.xx.109  Bcast:xx.xxx.xx.255  Mask:255.255.255.0
```(I've hidden my full inet addr with xx)

whereas you have inet addr:127.0.0.1    (local host)

---

### Post by spikoley on 2011-04-22
Your ifconfig doesn't show an IP address.  Try this command.

```
sudo dhcpd eth0
```

---

### Post by yossell on 2011-04-22
Hi spikoley, 
unfortunately, sudo dhcpd gives me a command not found.
 
Hi dragonfly,
thanks - I just entered that address from the ifconfig file in an attempt to manually tell the network where to look. I don't really know the significance of the address.
 
I probably had done some updating as I tend to install packages as they come up. I don't think I'd installed a new kernel for a while, and trying an older kernel didn't seem to help.

---

### Post by yossell on 2011-04-22
This has just got even more baffling.
 
I loaded up my live disk version of 10.04 - and the ethernet isn't working here either. If some update had broken my ethernet connection, then shouldn't the original 10.04 should still be working?
 
So what does that leave? As I say, everything works fine in windows. Is it possible that the hub (it's a BT-hub) has been silently updated by BT in such a way that it no longer talks to Linux properly? If so, does anybody know how I might manually put in the right settings?
 
Any ideas very gratefully received.
 
 
EDIT: no - it's not that. I've just put on a live cd of a version of slitaz up, and the auto ethernet is working fine there. Hmm....

---

### Post by yossell on 2011-04-22
Thanks spikoley,

I connected an old BT hub to the computer - which worked. I then installed the dhcpcd program (which I assumed was what you intended to suggest) and ran the command. 

This gave me an IP number.

I then brought up Network Connections, clicked edit the wired ethernet connection.

I then chose the tab IPv4 Settings and - hopefully - manually entered the IP number into the box that read DHCP client ID.

The connection then worked.

Thankyou very much for your help.

---

