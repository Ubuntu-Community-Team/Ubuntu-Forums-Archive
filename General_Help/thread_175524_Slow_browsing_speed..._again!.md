---
title: "Slow browsing speed... again!"
date: 2006-05-13
forum: General Help
---

### Post by ronniet on 2006-05-13
Hi all,

I had a problem with reeeeeally slow browsing speed a few weeks ago. Searched high and low on this forum and added the 'bad_list' file and that worked a treat. :KS 

Now, for some unknown reason, its happened again. Reeeeally slow browsing speed! :confused: 

Any ideas how to fix this problem once and for all? ](*,) 

**It's driving me nuts.**

I can still check email and download at full speed, its just the browsing that seems to be affected (same as last time).

IPV6 is off in *Firefox*. Tried *Evolution, Konqueror* and *Opera*. All the same. Slower than a week in jail. Have tried removing the 'bad_list' file to see if that'd help. Nothing.

Please help. It's quite warm today and the window is open, its a big temptation...  ;)  :D

---

### Post by richbarna on 2006-05-13
I use Epiphany on my slow old laptop, it seems quite quick.
Why not try it out ?
[http://ploum.frimouvy.org/?2006/03/15/100-why-you-should-try-epiphany-as-your-default-browser-with-gnome-214]("http://ploum.frimouvy.org/?2006/03/15/100-why-you-should-try-epiphany-as-your-default-browser-with-gnome-214")

---

### Post by ronniet on 2006-05-13
No, it's not a browser problem its an Ubuntu problem.

I fixed it before (with the bad_file thing) but even with that fix still in place i'm getting the problem again...

---

### Post by tsb on 2006-05-13
I'd try Swiftfox.

---

### Post by Kibbo on 2006-05-16
HI there,

I'm hardly an expert on this, but it could be a DNS problem.  Do downloads take awhile to resolve before they start?  Does the browser seem to hang when "looking up" the site, then finally find it and download it at a good speed?

Try using a static IP and setting your router to be the primary DNS.

---

### Post by ronniet on 2006-05-20
This one problem is the only thing stopping me from completely ditching Windows but if this keeps up i'll be heading back to 'the dark side'...  ](*,)   ](*,)

I've disabled IPV6 in Firefox (about:config)

I've added the bad_list file into etc/modprobe.d/

And now i'm about to throw myself out my bedroom window to see if that fixes it...  ](*,)  ;) 

How do I go about altering the IP and DNS settings? There's just so many settings and any time i alter one setting I have to put it back since i end up with no internet at all!

I have a **Linksys WAG54G** wireless router and a wireless ethernet card in my PC. In my network settings my router is **dis**abled and my ethernet card is **en**abled.

I know that set up might sound a bit weird but it worked fine when i had Hoary installed, well, it did for a little while, but i did a fresh install of Dapper and it was immediately slow...  :confused: 

All ideas considered. The windows open and i'm on the ledge...  ;)  :D

---

### Post by coolclassic on 2006-05-21
I have found this forum that covers slow internet speeds with your modem it may be worth looking at:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/515299.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/515299.html)

---

### Post by cyracks on 2006-05-21
[QUOTE=ronniet]
How do I go about altering the IP and DNS settings?[/QUOTE]

IP: (to change IP to 192.168.0.1 on eth0 interface)
```

sudo ifconfig eth0 192.168.0.1

```

DNS:
edit the file **/etc/resolv.conf**

To check if you have dns problem do the following:
1. get the IP of your dns server:
```

cat /etc/resolv.conf|grep nameserver

```
2. try to ping that dns servers (I assume you have 2 dns servers)
```

ping dns_server1
ping dns_server2

```
3.1 If everything ok try to query dns server
```

host www.google.com dns_server1
host www.google.com dns_server2

```
3.2 If not change dns server.

---

### Post by ronniet on 2006-05-21
Thanks guys, i'll give those ideas a go tomorrow.

Oh the shame... having to use Windows just now since I just couldn't put up with the slow browsing speed. Hopefully next time I reply it'll be from linux!  :)

---

### Post by ronniet on 2006-05-27
Ok, this is weird...

I've just come back to Kubuntu to try the above ping/host stuff and now my speed seems ok! _I've not changed a thing!_

Anyway; here's my results:

[I]**ronnie@kubuntu:~$** cat /etc/resolv.conf|grep nameserver
nameserver 205.188.146.145

**ronnie@kubuntu:~$** ping 205.188.146.145
PING 205.188.146.145 (205.188.146.145) 56(84) bytes of data.
64 bytes from 205.188.146.145: icmp_seq=1 ttl=127 time=24.0 ms
64 bytes from 205.188.146.145: icmp_seq=2 ttl=127 time=24.1 ms
64 bytes from 205.188.146.145: icmp_seq=3 ttl=127 time=23.6 ms
64 bytes from 205.188.146.145: icmp_seq=4 ttl=127 time=24.0 ms
64 bytes from 205.188.146.145: icmp_seq=5 ttl=127 time=669 ms
64 bytes from 205.188.146.145: icmp_seq=6 ttl=127 time=22.4 ms
64 bytes from 205.188.146.145: icmp_seq=7 ttl=127 time=22.6 ms
64 bytes from 205.188.146.145: icmp_seq=8 ttl=127 time=25.2 ms
64 bytes from 205.188.146.145: icmp_seq=9 ttl=127 time=23.2 ms

--- 205.188.146.145 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8005ms
rtt min/avg/max/mdev = 22.438/95.408/669.259/202.888 ms

**ronnie@kubuntu:~$** host [www.google.com](www.google.com) 205.188.146.145
Using domain server:
Name: 205.188.146.145
Address: 205.188.146.145#53
Aliases:

[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 64.233.183.104
[www.l.google.com](www.l.google.com) has address 64.233.183.147
[www.l.google.com](www.l.google.com) has address 64.233.183.99
[www.l.google.com](www.l.google.com) has address 64.233.183.103
Using domain server:
Name: 205.188.146.145
Address: 205.188.146.145#53
Aliases:

[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
Using domain server:
Name: 205.188.146.145
Address: 205.188.146.145#53
Aliases:

[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).[/I]

Some of which makes no sense to me but it's just quite annoying how this 'bug' seems to repair itself. Thats the one thing I hate about Windows! It's self-repairing bugs!... *agghhh*... hope Dapper final fixes this kinda thing...   :/

---

### Post by cyracks on 2006-05-27
[QUOTE=ronniet]
[I]**ronnie@kubuntu:~$** cat /etc/resolv.conf|grep nameserver
nameserver 205.188.146.145
[/QUOTE]

Since you have only one dns server that could be the source of your problem.
Try to add another dns server.

---

### Post by ronniet on 2006-05-27
umm...
*embarassed*

how do i add another DNS server?
Is it a setting in my router? Or in Kubuntu?

Sorry to be a bit of a dumba$$  :(

---

### Post by ronniet on 2006-05-27
Oh, and just out of curiosity :
How come it doesn't seem to affect my Windows' browsing speed?

Or is this where curiosity kills the cat??   ;)  :D

---

### Post by cyracks on 2006-05-27
[QUOTE=ronniet]Oh, and just out of curiosity :
How come it doesn't seem to affect my Windows' browsing speed?
[/QUOTE]

If you have a problem with dns server then write in cmd something like
```

ipconfig /all

```
and copy the second dns server to /etc/resolv.conf

---

### Post by ronniet on 2006-05-27
Even in Windows I only have one DNS Server :


Windows IP Configuration
        Host Name . . . . . . . . . . . . : rtj
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NETGEAR 108 Mbps Wireless PCI Adapter WG311T
        Physical Address. . . . . . . . . : 00-09-5B-C7-69-8A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 205.188.146.145
        Lease Obtained. . . . . . . . . . : 27 May 2006 16:58:13
        Lease Expires . . . . . . . . . . : 28 May 2006 16:58:13

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VIA Compatable Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-0C-6E-86-9C-88
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

**Weird...**

---

### Post by karloz on 2006-05-28
I had the exact same problem for these last two days.  The problem was happening with wireless and wired connections.  I know it had to do with DNS, but I was putting in the exact same settings as the XP settings, on the same exact dual booted laptop.  I had trouble pinging the gateway, the DNS servers, and even my OWN IP ADDRESS at times.  Sometimes I could get to my routers GUI (192.168.0.1), and sometimes I couldn't.  Sometimes I could browse by IP, sometimes I couldn't.  I was sometimes able to bring up pages by their URL, but it took forever to find them.  I tried installing dhcpd and it didn't help.  After going in circles I decided to try installing Network-Mangager.  After about 10 tries using Synaptic Package Manger it finally downloaded and installed it.  I used Sessions under preferences to load it at startup, logged out and back in, connected to my router and IT WORKED!!!  I'm now able to browse perfectly fine!!!  I know there were two more packages that installed with NetworkManager, but I didn't pay attention to what they were.  Something that was installed definitely did fixed my problem though.

---

### Post by ronniet on 2006-05-29
**thanks for that tip karloz.**

I'm gonna wait now until the final release of Kubuntu Dapper Drake comes out on (hopefully) Thurs/Fri this week. I'll do a complete fresh install (hadn't installed anything on Dapper flight7 anyway) and see how that goes. If it still screws up my browsing speed then i'll try your Network Manager tip.

Thanks for all the help folks, i really appreciate it.

---

### Post by cjptopher on 2006-06-08
I had this problem too for both wired and wireless browsing and it was to do with the default DNS entries.

I have a dual boot laptop
On WinXP "ipconfig /all" gives:
DHCP: 192.168.1.1
Gateway: 192.168.1.1
DNS: 192.168.1.1

On a newly installed Dapper 6.06 under the DNS tab of "Network Settings" or "/etc/resolv.conf" I had:
202.96.128.68
202.96.134.188
202.106.0.20
202.106.46.151

After deleting each DNS server apart from "202.106.46.151" things worked fine. Deleting "202.106.46.151" and adding "192.168.1.1" was even better.

By the way, be careful using PING to diagnose these problems because it is often disabled on servers and so you get an unreachable host when in fact the server will respond fine to requests it is meant to deal with. For example "host [www.google.cn](www.google.cn) IP" is OK when "ping IP" fails. -> In China [www.google.com](www.google.com) rarely works :-) 

In my case the bad DNS values (202.96.128.68, 202.96.134.188 & 202.106.20) seem to come from my router where they are available under some page to do with WAN setup. I will make a guess that DHCP replies include this information and my dapper install is using it instead of the router address. Maybe this is strictly the correct way to behave but in reality doesn't work so well. I suppose that WinXP gets it right by either defaulting to the router address or more likely testing the DNS IPs to see if they work before using them.

I seemed to recall reading in the forums that Ubuntu used to default to the router address for DNS but this caused problems and now they have changed to use the proper field supplied by DHCP. If so then in the real world this doesn't work so well as not all router manufacturers correctly implement DHCP. Just guessing though.

christopher

---

### Post by karloz on 2006-06-08
Well I didn't try pinging the DNS servers from XP, but one of the DNS servers is my router IP, and that ip is able to be pinged because I'm doing it right now in my working Ubuntu OS.  I know for a fact I had the right settings, and I know for a fact that it had nothing to do with the router.  I'm guessing it had something to do with the OS at the time, and maybe some bad, missing, or corrupted files.  Even a fresh install didn't allow me to browse correctly using an ethernet connection.  But since I've installed NetworkManager my ethernet and wireless connection are working perfectly.

---

### Post by michaelphipps on 2006-07-07
Hi,

I just wanted to say - I was experiencing the same problem.  And after reading a few bits and pieces I worked out how to fix it.

I use DHCP, so when my DNS settings were set they were set in the following order:

10.0.0.139 (my router)
139.130.4.4 (my ISP DNS Server)

Network things were slow.  I switched the order of these two details in the system settings panel > Network Settings > Domain Name System 

so the order was now my isp dns server first, then my router ip

Everything works much quicker now.

---

### Post by srhalfwaythere on 2006-07-13
@michaelphipps
I tried what you said and it worked right away.
Before trying your way I had did what a previous post said about IPv6. I commented out a line and added off to the others. That really didnt seem to work much.
I probably shouldn't, but I'm also going to add that network-manager program, maybe it'll help things out even more.
Good luck to all the others with this probelm, I recommend trying what michaelphipps said in the post before me.

---

### Post by srhalfwaythere on 2006-07-15
I'v got a problem now with this. Every time I start up ubuntu, I have to change the order of the dns servers so that the router is last. Is there a way to have it automatically set router to the last one?

---

