---
title: "Internet not working"
date: 2010-10-14
forum: General Help
---

### Post by philpp on 2010-10-14
Hey all,
I just installed Ubuntu Server 10.10 and I can't get the internet to work.

When I was installing Ubuntu, I selected wlan0 to be the main internet thing or whatever, but now I don't want to use wireless so I just plugged an ethernet cable into the computer, but it's still not working. I have a broadband cable modem.

When I type ifconfig -a, it lists virbr0 and eth0. eth0 has only an ipv6 address but virbr0 has both v4 and v6. I can't ping google.com or 192.168.1.1.

---

### Post by MooPi on 2010-10-14
Can you post the results of your ifconfig -a
Also can you give us /etc/network/interfaces contents ?

---

### Post by philpp on 2010-10-14
ifconfig -a:

```

eth0	Link encap:Ethernet  HWaddr 00:16:76:e1:83:fe
		inet6 addr: fe80::216:76ff:fee1:83fe/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:24 errors:0 dropped:0 overruns:0 frame:0
		TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000
		RX bytes:2925 (2.9 KB)  TX bytes:2520 (2.5 KB)
		Iterrupt:20 Memory:e3200000-e3220000

lo		Link encap:Local Loopback
		inet addr:127.0.0.1  Mask:255.0.0.0
		inet6 addr: ::1/128 Scope:Host
		UP LOOPBACK RUNNING  MTU:16436  Metric:1
		RX packets:38 errors:0 dropped:0 overruns:0 frame:0
		TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:0
		RX bytes:2892 (2.8 KB)  TX bytes:2892 (2.8 KB)

```

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

	address 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are <ommited>
	dns-nameservers 192.168.1.1
```

Note though, I tried setting it up with DHCP but it didn't work, so I entered some stuff manually like 192.168.1.1 for the things, and whatever. I probably just messed it up though.

---

### Post by MooPi on 2010-10-14
How about /etc/network/interfaces ?

---

### Post by philpp on 2010-10-14
> **MooPi said:**
> How about /etc/network/interfaces ?

Edited and appended :)

Also,

sudo ifconfig eth0 up

works but

sudo dhclient eth0

times out and it says it got no "DHCPOFFERS".

---

### Post by MooPi on 2010-10-14
You could edit your interfaces file , make itr look something like this 
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by philpp on 2010-10-14
> **MooPi said:**
> You could edit your interfaces file , make itr look something like this 
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I did that and restarted, it didn't do anything.

---

### Post by MooPi on 2010-10-14
But sudo ifconfig eth0 up works ?

---

### Post by philpp on 2010-10-14
> **MooPi said:**
> But sudo ifconfig eth0 up works ?

Yes

---

### Post by MooPi on 2010-10-14
So your problem is solved ?

---

### Post by philpp on 2010-10-14
> **MooPi said:**
> So your problem is solved ?

Nope. ifconfig eth0 up works but I have no internet.

---

### Post by nnymous12 on 2010-10-14
I have a similar problem (posted it here: [http://ubuntuforums.org/showthread.php?t=1597027](http://ubuntuforums.org/showthread.php?t=1597027))
Can you help, please?

(- sudo ifconfig eth0 up, [as in your conversation string] seems not to work, but I also do not know how to check other than to look whether the internet browser works
- tried to edit /etc/network/interfaces, but have no permission to save the file ([am administrator])

/etc/network/interfaces contents:
auto lo
iface lo inet loopback

from ifconfig -a I get:
Version:1.0 StartHTML:0000000167 EndHTML:0000003323 StartFragment:0000000454 EndFragment:0000003307    	 	 	 	p { margin-bottom: 0.21cm; }  eth0      Link encap:Ethernet  HWaddr 00:1c:23:8f:dc:fe   
           inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0  
           inet6 addr: fe80::21c:23ff:fe8f:dcfe/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:285 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:851 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:43491 (43.4 KB)  TX bytes:82389 (82.3 KB)  
           Interrupt:21  
 

 eth1      Link encap:Ethernet  HWaddr 00:1c:26:3a:d9:fd   
           inet6 addr: fe80::21c:26ff:fe3a:d9fd/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:18  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:18 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:18 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:1168 (1.1 KB)  TX bytes:1168 (1.1 KB)  
 

 vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00   
           BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Toz on 2010-10-14
The problem is that you are not getting a reply to your DHCP request. Is the ethernet cable plugged directly into your cable modem? If so, double-check the connections. With your typical cable modem, you should be able to get an connection with a DHCP request.

---

### Post by nnymous12 on 2010-10-14
sorry, not sure what a DHCP request is, but the other computer on the same box works, and I checked all connections, swapped the cables.

---

### Post by philpp on 2010-10-14
No, I just plugged another computer in with the same cable and it got a DHCP reply.

---

### Post by Toz on 2010-10-15
@nnymous12: what do you mean by "other computer on the same box"? Did you plug another computer directly into the broadband modem? I also notice that you have 2 network adapters in your computer (eth0 & eth1). You might want to try 'sudo ifconfig eth1 up' in case your cable is plugged into that card. Also, to edit the /etc/network/interfaces file, make sure you do so with sudo ala 'sudo gedit /etc/network/interfaces'.

@philpp: hmmm - maybe the network card is bad? Can you try starting the computer with the Ubuntu LiveCD and see if you get an internet connection that way? Also, can you have a quick peek at the back of the computer where you plug the cable in - is there a green light there?

---

### Post by Toz on 2010-10-15
You might also want to have a look at this page: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) for information regarding NetworkManager and getting it to manage the network connectivity for you - which is the default in Ubuntu.

---

### Post by nnymous12 on 2010-10-16
Thanks, Toz! (still not there yet...)

- 'other computer on the same box': I have a DSL modem, on which I have a wireless box.  The wireless box has 4 positions for cables. Wireless works (with the other computer), also the other computer has internet when I turn the wireless off and plug the cable (coming from any one of the 4 positions on the wireless box) that usually goes to my ubuntu computer into the other computer.
- 'sudo ifconfig eth1 up' seems not to change anything. But besides the little icon with the two screens not changing, the only way I know how to test the internet connection is to run firefox, which does not get into the net.
- 'sudo gedit' took care of my permission problem saving 'interfaces', but putting 
'auto eth0   
iface eth0 inet dhcp'  into 'interfaces' and restarting the computer did not get me into the internet.
I reverted to the previous text
- I am working on network manager, but looking at the page you linked to, there is something  messed up in my system: when I click the nm icon, I get (greyed out) 'no network devices available' and (activatable) 'VPN connections', under which I get the configuration window from 'configure VPN'. i.e. the starting options of nm are already very different from the description on the web page.
-I am still playing around with nm, will get back to you

---

### Post by nnymous12 on 2010-10-16
It does not look like I can make this work using nm.
I tried following the instructions, but can't make the system work
does the response I got to
	 	 	 	 	 	 	 	 	  'dmesg | grep eth' have anything to do with the problem?:


    	 	 	 	 	 	 	 	 	 	  [   19.195115] eth0: Broadcom BCM4311 802.11 Hybrid Wireless Controller 5.60.48.36  
 [   19.314216] b44 ssb0:0: eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:08:C7:1B:8C:03
 [   19.356784] udev[336]: renamed network interface eth1 to eth1-eth0  
 [   19.369776] udev[337]: renamed network interface eth0 to eth1  
 [   19.416751] udev[336]: renamed network interface eth1-eth0 to eth0  
 [   19.427989] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   22.820208] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex  
 [   22.820215] b44 ssb0:0: eth0: Flow control is off for TX and off for RX  
 [   22.820584] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  
 [   30.336045] eth1: no IPv6 routers present  
 [   32.868029] eth0: no IPv6 routers present

---

### Post by nnymous12 on 2010-10-16
P.S.: the icon next to nm (looks like a grey ball on a yellow stick) says 'connection manager demon is not running', when I pull the cable out and plug it back in the icon changes to look like the cable plug with a red circle and when clicked it has 'disconnect network'.  does that mean anything?

---

### Post by Toz on 2010-10-17
when you left-click on the icon, what do you see?

when you right-click on the icon, what do you see? Is "Enable Networking" selected? What does "Connection Information" show?

And just to confirm, does your /etc/network/interfaces file still look like:
> auto lo
iface lo inet loopback

---

### Post by nnymous12 on 2010-10-20
Before I answer your questions:
BUMMER! I had enough of the computer not having internet and booted from the Ubuntu 10.10 disk.  WIred internet worked right away.  (WIreless not yet, I have a feeling I need to get the SSID right in the network settings, will look for instructions.)
This is good news since it means the hardware works, but bad new because if I can not fix the problem, I'll have to re-install the operating system and I had put a lot of work into customizing that...
To your questios:
- my interfaces file still is:
auto lo
iface lo inet loopback
- when I left click the nm icon, I get (greyed out) 'no network devices  available' and (activatable) 'VPN connections', under which I get the  configuration window from 'configure VPN
-when I right click, 'enable networking' exists, but is greyed out. 
- Under 'connection information' I get the same wndow as from 'configure VPN', it has no connections pre-filled in, I can click 'add' and follow the instructions on the web site, but can not make the network work that way.

---

### Post by fat tubby on 2010-10-20
thanks i had same problem

---

