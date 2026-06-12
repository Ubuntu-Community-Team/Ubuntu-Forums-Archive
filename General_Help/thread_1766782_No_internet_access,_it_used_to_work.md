---
title: "No internet access, it used to work"
date: 2011-05-24
forum: General Help
---

### Post by halibaitor on 2011-05-24
When I turned my desk top on this afternoon I could not access the internet.  It worked this morning. When I look at the Network Connections it tells me that Auto eth0 was last used "never", and I currently have No Network connection.

I am using Ubuntu 10.10.

Is there anything I might do to restore the connection other than a full install?  What went wrong?  Everything seemed normal when I shut it down this morning.  Any ideas?

---

### Post by doas777 on 2011-05-24
please open a terminal (Applications -> Accessories) and post back the output of these commands:

```

sudo ifconfig -a
nslookup www.ubuntuforums.org
cat /etc/network/interfaces
cat /etc/resolv.conf

```this sounds like a simple networking issue, so no need to be thinking about reinstalling (at least not yet).

---

### Post by halibaitor on 2011-05-24
Do I enter that all at once, or a line at a time ?  Sorry to be so lame, but I'm kinda new at this Ubuntu stuff.

---

### Post by doas777 on 2011-05-24
> **halibaitor said:**
> Do I enter that all at once, or a line at a time ?  Sorry to be so lame, but I'm kinda new at this Ubuntu stuff.
my appologies. 
one line at a time.
you can copy into/paste out of a terminal with rightclicks or by using Ctrl+Shift+C and Ctrl+Shift+V

---

### Post by linuxinstalledfromhdd on 2011-05-24
They need one command that does all four of those commands. :) 

I made a little bash script file and put it into my common path directory.  It's great.

---

### Post by halibaitor on 2011-05-24
this be strange.  I got a bunch of stuff on the first line, but no easy way to get it out of the desktop to this netbook so i can post it...  I'm gonna have to put it on a jump drive to transfer it.  It will take a few minutes.

---

### Post by halibaitor on 2011-05-24
OK...  here is the output from the first line.  Since there is no internet connection the rest of it failed.


&#65279;eth0      Link encap:Ethernet  HWaddr 00:c0:f0:5a:27:81  
          inet6 addr: fe80::2c0:f0ff:fe5a:2781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:7 dropped:0 overruns:0 carrier:14
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45998 (45.9 KB)  TX bytes:45998 (45.9 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by linuxinstalledfromhdd on 2011-05-24
Power cycle your entire network (in this order, modem, router, PC)  and run those commands again. See if you have anything different showing. 

Repost the results so we can compare as well.

---

### Post by halibaitor on 2011-05-24
This is a bit different...

eth0      Link encap:Ethernet  HWaddr 00:c0:f0:5a:27:81  
          inet6 addr: fe80::2c0:f0ff:fe5a:2781/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:5 dropped:0 overruns:0 carrier:10 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2119 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2119 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:78900 (78.9 KB)  TX bytes:78900 (78.9 KB) 

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

terry@terry-HP-d220-MT-DG266A:~$ nslookup [www.ubuntuforums.org](www.ubuntuforums.org) 
;; connection timed out; no servers could be reached 

terry@terry-HP-d220-MT-DG266A:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

terry@terry-HP-d220-MT-DG266A:~$ cat /etc/resolv.conf 
# Generated by NetworkManager 
nameserver 192.168.10.1

---

### Post by linuxinstalledfromhdd on 2011-05-24
Ok, next to a physical inspection of all your network cable connections.  All of them. Maybe something creeped out over time.  If that isn't it, does the live disc have internet when you boot from that?

---

### Post by doas777 on 2011-05-24
@Op, you don't have an IP address so lets try this.
in your terminal enter:
```

gksu gedit /etc/network/interfaces

```then below the lines you already have, add:
```

auto eth0
auto eth0 inet DHCP

```and save the file. 
then run this command to restart networking on your PC:
```
sudo /etc/init.d/networking restart
```then run ifconfig -a again and post the results back

---

### Post by halibaitor on 2011-05-24
I tried the CD and there was no internet there either, so I just tried using Windoze.  No internet there either, and it says a cable is unplugged.  The cables are good (I've tried 2 different wires), so I'm thinking the router took a dump while I wasn't looking, but the wireless part is working just fine cause I'm still using that.  

Odd combination, but I'm gonna look for another router to swap out and see if that solves the problem.  I'm guessing that the output looks like the OS and computer are working?

Thanks for your prompt assistance.  You guys are very helpful. :)

---

### Post by doas777 on 2011-05-24
> **halibaitor said:**
> I tried the CD and there was no internet there either, so I just tried using Windoze.  No internet there either, and it says a cable is unplugged.  The cables are good (I've tried 2 different wires), so I'm thinking the router took a dump while I wasn't looking, but the wireless part is working just fine cause I'm still using that.  

Odd combination, but I'm gonna look for another router to swap out and see if that solves the problem.  I'm guessing that the output looks like the OS and computer are working?

Thanks for your prompt assistance.  You guys are very helpful. :)

the output of the ifconfig command showed that you were not participating in the network, but with these tools, that's all we can tell. 

ethtool could tell us more about the state of your NIC, but unfortunately the time you most need ethtool, is the time you can't get an internet connection to install ethtool. 

you might want to try jacking into a different port on your router, and if you have a spare cable, might as well try it out.

---

### Post by halibaitor on 2011-05-24
> **doas777 said:**
> 
you might want to try jacking into a different port on your router, and if you have a spare cable, might as well try it out.

I tried that with no success.  I also tried plugging the output of the modem directly into the computer.  That seemed like it was going to work, but also failed.

---

### Post by doas777 on 2011-05-24
> **halibaitor said:**
> I tried that with no success.  I also tried plugging the output of the modem directly into the computer.  That seemed like it was going to work, but also failed.
interesting. did you duplicate that result in windows and perhaps the live cd?

---

### Post by halibaitor on 2011-05-24
> **doas777 said:**
> interesting. did you duplicate that result in windows and perhaps the live cd?

Good thought.  I tried it and failed with both.  

So I've changed my mind.  I'm thinking it is a hardware problem with the computer.  I'm going to look for a 10/100 card or a wireless card for it and hope Ubuntu recognizes one of them...  I think I have both cards laying around somewhere, I just gotta find them in the junk pile.  The router almost has to be working like it is supposed to.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Contact your ISP. Begin a trouble ticket. You found out that it's not just Ubuntu.  They will resolve it.

---

### Post by halibaitor on 2011-05-24
I installed a 10/100 card, Ubuntu recognized it and I'm back online.  :D

Sorry to have bothered you with a problem that wasn't with the OS.:redface:

You guys are great!!!  Thanks.  I owe you one.

---

### Post by doas777 on 2011-05-24
no problem man. network troubleshooting is standard fare around here. 
cheers

---

