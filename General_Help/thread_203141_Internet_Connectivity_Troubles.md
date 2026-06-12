---
title: "Internet Connectivity Troubles"
date: 2006-06-24
forum: General Help
---

### Post by stubadub on 2006-06-24
I've tried installing Ubuntu, Kubuntu and Xubuntu from the live cds and all have given me the following problem.  While using the live cds I have absolutely no problems connecting to the internet and pulling up web pages.  Once I decide to install and reboot the machine I am unable to connect to the internet any longer.  I verified that my network card is activated but I'm not sure where to go from here.  I did not have this problem while running 5.10.  I've looked for information that might help fix this issue, but haven't found any threads that help.  Does anyone have any ideas?

---

### Post by woedend on 2006-06-24
by chance can you post your /etc/network/interfaces  file contents and  the output of ifconfig  from your installation(not the live cd of course).
Also, whats your setup?  Ethernet/dialup/router/?

---

### Post by handy on 2006-06-24
I have to enter **about:config** in the Firefox address field, then **ipv6** in the Firefox filter field.  Then double click on the one & only line that is displayed to change the boolean value to **True**.  
That's it for IPv6 - then I can browse the web, & not before!

To be able to use the repositories, I have to put my ISP's DNS addresses in the **Menu: System / Administration / Networking - DNS tab**

Again, if I don't do that - NO repo's!

I hope that helps you? :KS

---

### Post by stubadub on 2006-06-25
@woedend

My setup is ethernet through a Netgear nat router.

Here's the interfaces file output:
auto lo
iface lo inet loopback

atuo eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Here's the result of running ifconfig:

eth0 Link encap:Ethernet HWaddr 00:80:AD:74:55:A2
       inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
       inet6 addr: fe80::280:adff:fe74:55a2/64 Scope:Link
       UP BROADCAST MULTICAST  MTU:1492  Metric:1
       RX packets:29  errors:160  dropped:0  overruns:0  frame:0
       TX packets:18  errors:1  dropped:0  overruns:0  carrier:1
       collisions:0  txqueulen:1000
       RX bytes:4721 (4.6 KiB)  TX bytes:1808 (1.7 KiB)
       Interrupt:201  Base address:0xe800

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr:  ::1/128  Scope:Host
       UP LOOPBACK RUNNING  MTU:16436  Metric:1
       RX packets:3  errors:0  dropped:0  overruns:0  frame:0
       TX pacekts:3  errors:0  dropped:0  overruns:0  carrier:0
       collisions:0  txqueuelen:0
        RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

---

### Post by stubadub on 2006-06-25
@Handy

I tried changing that boolean value to True, but it didn't have any effect.  I do appreciate the suggestion though.  Do I need to add my ISP's DNS anyway?  I'll try to locate that info now.

---

### Post by handy on 2006-06-25
[QUOTE=stubadub]@Handy

I tried changing that boolean value to True, but it didn't have any effect.  I do appreciate the suggestion though.  Do I need to add my ISP's DNS anyway?  I'll try to locate that info now.[/QUOTE]

I just had a look at the router config' through firefox, for my Netgear DG632:

IP address: 192.168.0.1
User: admin  
Password: password

I find 2 **D**omain **N**ame **S**erver addresses, right below the** Gateway IP Address** listed on the **Router Status** page.

These are the 2 addresses I use in the Ubuntu network config' as mentioned in previous post.

Your Netgear router/modem will probably(?) give you access the same way.  Have a look at the label on the router, it should give you its IP address & the Username & Password on the label - mine does!

Leave the ipv6 turned off in Firefox.  It will do you no harm & potentially a lot of good!

---

### Post by stubadub on 2006-06-25
I cannot access the router with the installed version, I just get an error that says it cannot find that address.  When I try to do the same thing from another pc hooked up to the router or from the problem pc using the live cd I have no problem and see the router's admin page. How odd.

---

### Post by handy on 2006-06-26
[QUOTE=stubadub]I cannot access the router with the installed version, I just get an error that says it cannot find that address.  When I try to do the same thing from another pc hooked up to the router or from the problem pc using the live cd I have no problem and see the router's admin page. How odd.[/QUOTE]

If you are still in trouble, I'd suggest you post in the **Hardware / Networking** forum.

---

### Post by blushores on 2006-08-04
Hi,
I was having problems accessing the Internet as well. I could connect to my Router(Netgear WPN824) and ADSL modem(Netgear DG632), but not the Internet. 

The following solution worked for me: 

I did what Handy suggested in this Post [http://www.ubuntuforums.org/showpost.php?p=1178495&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=1178495&postcount=3")

Go to System > Administration > Networking. 
Click on the DNS tab and add the domain name servers (DNS) to that. 

These 2 changes fixed my problem. 

Now I have to fix the PS2 mouse. ;)

---

### Post by eXisor on 2006-08-04
stubadub:

It's likely you're running both 'dfme' and 'tulip' as netwrk drivers for your card. To check, type 'lsmod' into a terminal.
If you see both dfme and tulip you have the problem. To fix..
```
sudo gedit /etc/modprobe.d/blacklist
```
Add 'tulip', w/o the quotes to the bottom of the file and reboot.

---

