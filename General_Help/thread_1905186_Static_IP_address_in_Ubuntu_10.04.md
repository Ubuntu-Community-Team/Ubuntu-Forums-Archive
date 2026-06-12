---
title: "Static IP address in Ubuntu 10.04"
date: 2012-01-06
forum: General Help
---

### Post by carranty on 2012-01-06
I have two desktop computers which connect to the internet wirelessly via a Netgear router.  I often remotely login to one from the other to transfer files but the IP adress of each is different each time I do.  I have to use nmap to figure out the IP address of the remote each time before I can log in, it doens't take long, but I'm sick of doing it.  How do I go about setting up each computer so it will use the same IP address each time?

My /etc/network/interfaces file only has the two lines
```

auto lo
iface lo inet loopback
```

no mention of wlan0.

---

### Post by ajgreeny on 2012-01-06
To solve a similar problem with my machines also on a Netgear router I have used the netgear setup to use Reserved IP adresses for machines, including a wireless printer.  It all seems to work faultlessly.

On my router the setting is in LAN settings.  See screenshot.

---

### Post by Lars Noodén on 2012-01-06
> **carranty said:**
> no mention of wlan0.

What is the current output from [ifconfig](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html) with your dynamically generated IP address? We can use that to figure out the settings for a static address.

---

### Post by carranty on 2012-01-06
> **ajgreeny said:**
> To solve a similar problem with my machines also on a Netgear router I have used the netgear setup to use Reserved IP adresses for machines, including a wireless printer.  It all seems to work faultlessly.

On my router the setting is in LAN settings.  See screenshot.

Ah ok, so I just add the MAC address of the computers to this list and the router will always issue them the same IP.  Thanks

Out of curiosity I'd still be interested to learn how to do this from within Ubuntu itself.

[QUOTE=Lars Noodén]
What is the current output from [ifconfig]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html") with your dynamically generated IP address? We can use that to figure out the settings for a static address.     
[/QUOTE]


```
carranty@carranty-desktop ~ $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0e:0c:c6:88:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:15:58:97:8e:96  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18168 (18.1 KB)  TX bytes:18168 (18.1 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4a:ca:1d  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe4a:ca1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6432469 (6.4 MB)  TX bytes:905881 (905.8 KB)
```Most of the tutorials I've read basically say to add the following to my interfaces file

```
auto wlan0
 iface wlan0 inet static  
       address *.*.*.*      
   netmask *.*.*.*       
  network *.*.*.*       
  broadcast *.*.*.*      
   gateway *.*.*.*
```but don't explain what numbers you should type. Am I right in thinking address is the IP you want and gateway is the router?  Are broadcast and netmask the values of Bcast and Mask in the ifconfig output?  What about network?

EDIT : Also, many guides also say something along the lines of *"If you want to add a static DNS server, you&#8217;ll need to edit the /etc/resolv.conf file".  *What is a static DNS server, and do I want one?

---

### Post by Lars Noodén on 2012-01-06
> **carranty said:**
> 
but don't explain what numbers you should type. Am I right in thinking address is the IP you want and gateway is the router?  Are broadcast and netmask the values of Bcast and Mask in the ifconfig output?  What about network?

Yes, the gateway is the router or you can find it with [route](http://manpages.ubuntu.com/manpages/oneiric/en/man8/route.8.html) with no options.  Everything else (netmask, broadcast, etc) is there in the output from [ifconfig](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html).

The way ajgreeny suggest is good too if it works with your router.  MAC addresses can be changed manually so the are not good for absolute identification but they work well enough for the job here since it just you.

---

### Post by carranty on 2012-01-06
> **Lars Noodén said:**
> Everything else (netmask, broadcast, etc) is there in the output from [ifconfig]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html").

Sorry, but what should I put as the network value? Is it just 192.168.0.0?

---

### Post by Lars Noodén on 2012-01-06
Guessing from the output:

```

iface wlan0 inet static
   address 192.168.0.6
   broadcast 192.168.0.255
   netmask 255.255.255.0
   gateway 192.168.0.1

```

I'm not sure of the gateway.  That will be the address of your router.

One of these days, we're all going to have to get going and learn IPv6 instead.

---

### Post by carranty on 2012-01-07
Ok, so when I boot up my computer with the below in my interfaces file I have no network access at all (I can't browse the web, my dropbox doesn't sync and all pings fail - I can't even ping my own router).  What am I doing wrong?

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

---

### Post by efflandt on 2012-01-07
Unless you uninstalled NetworkManager, it would be easiest to use that.  In Lucid you would normally change settings in X from **System** > **Preferences** > **Network Connections**, or by right clicking on network applet in upper right and selecting **Edit Connections**.

Or from terminal or console you would need to **sudo nano** (or editor of choice) the proper file in /etc/NetworkManager/system-connections/ for your wireless and edit these parts like so (assuming your router is 192.168.0.1 and handles DNS):

[ipv4]
method=manual
dns=192.168.0.1;
addresses1=192.168.0.3;24;192.168.0.1;
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false

However, that is just an example from what you showed so far.  You should use a static IP in same network, but "outside" of the DHCP assigned range of your router LAN to avoid IP conflicts.  And there is more to that file than the above, especially for wireless security

Note, when connected once with automatic IP (DHCP), besides **ifconfig** which you already posted, check **route -n** (default gateway, ie router IP), and contents of /etc/resolv.conf [nameserver(s)].

If you uninstalled NetworkManager it would help if you say what you are using, or you can completely manually set everything (sudo or as root) with **ifconfig** and **route** commands and editing or copying to **/etc/resolv.conf**

---

### Post by carranty on 2012-01-07
> **efflandt said:**
> If you uninstalled NetworkManager it would help if you say what you are using

I didn't uninstall network manager, I was really just experimenting in order to learn how Ubuntu works a little better.  I was trying to setup a static IP by editing configuration files rather than using the GUI.

> **efflandt said:**
> , or you can completely manually set everything (sudo or as root) with **ifconfig** and **route** commands and editing or copying to **/etc/resolv.conf**


How would I do that?  A link to a how to guide would be much appreciated!

---

### Post by Dennis N on 2012-01-07
> **carranty said:**
> I have two desktop computers which connect to the internet wirelessly via a Netgear router.  I often remotely login to one from the other to transfer files but the IP adress of each is different each time I do.  I have to use nmap to figure out the IP address of the remote each time before I can log in, it doens't take long, but I'm sick of doing it.  How do I go about setting up each computer so it will use the same IP address each time?


[edit: overlooked that you are on wireless - the following is for wired. This procedure may work for wireless too, but with obvious modifications in the selections. I'll leave it as is, since it may be useful for someone else.]

My advice: Leave the interfaces file alone and use the network manager dialog. Here is how to proceed in Ubuntu 10.04 from my own notes:

> 
Right click on networking icon on the panel, select Edit Connections.
Select Wired Tab.
Select Auto eth0.
Click the edit button.
Change connection method to manual.
Click the add button.
Inside the dialog box, enter:
a) desired IP address (example: 192.168.2.50) 
b) net mask 255.255.255.0
c) gateway IP address (your router's ip address - mine is 192.168.2.1)
be sure to hit Enter after entering the last field
d) DNS servers = use gateway address (OR addresses of another DNS server you want to use)
e) uncheck the 'for all users' box at the bottom. (if not, it did not accept the changes)
f) hit apply

New connection may be made automatically, if not, use the network icon to reconnect.

I've used this on three 10.04 machines without problem to set a static IP.

---

### Post by carranty on 2012-01-07
> **Dennis N said:**
> 
I've used this on three 10.04 machines without problem to set a static IP.

I've just tried doing it this way also, same problem as before.  Once I enter the info and reconnect to the network it establishes the connection ("NETGEAR connection established") but I can't do anything (browse web/ping router etc).  I used the same values as posted earlier and have tried several different addresses.

---

### Post by Dennis N on 2012-01-07
> **carranty said:**
> I've just tried doing it this way also, same problem as before.  Once I enter the info and reconnect to the network it establishes the connection ("NETGEAR connection established")

Did you verify that it is connecting using the new IP address you gave it by checking the output of ifconfig?

---

### Post by carranty on 2012-01-07
> **Dennis N said:**
> Did you verify that it is connecting using the new IP address you gave it by checking the output of ifconfig?

Yes, it does.  Right now I'm back to using "Automatic (DHCP)" under the IPv4 tab

```
carranty@carranty-desktop ~ $ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4a:ca:1d  
         ** inet addr:192.168.0.7**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe4a:ca1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:716627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1021667842 (1.0 GB)  TX bytes:45978368 (45.9 MB)
```and I have network access

```
carranty@carranty-desktop ~ $ ping www.ubuntuforums.com
PING www.ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=50 time=29.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=50 time=29.4 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=50 time=30.7 ms
^C
--- www.ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 29.475/29.971/30.790/0.600 ms
```
If I then change to "Manual", enter the values previously listed, disconnect from NETGEAR and then reconnect
```

carranty@carranty-desktop ~ $ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4a:ca:1d  
         ** inet addr:192.168.0.3**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe4a:ca1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:716651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1021672807 (1.0 GB)  TX bytes:45992665 (45.9 MB)
```But now I have no network access
```

carranty@carranty-desktop ~ $ ping www.ubuntuforums.com
ping: unknown host www.ubuntuforums.com
```What am I supposed to put as the DNS server?  I thought it was the contents of this file
```

carranty@carranty-desktop ~ $ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 192.168.0.1
```I've been using this or leaving the field blank.  Maybe that's where I'm going wrong.....

---

### Post by Dennis N on 2012-01-07
> **carranty said:**
> What am I supposed to put as the DNS server?  I thought it was the contents of this file
```

carranty@carranty-desktop ~ $ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 192.168.0.1
```I've been using this or leaving the field blank.  Maybe that's where I'm going wrong.....

You can specify a different DNS server in the same dialog used when editing the connections. There is a box there for that. If left blank, I believe it uses the one specified by your ISP (which can be found in your router interface). 

I use Google DNS server (its far quicker than my ISP) and enter these values:

8.8.8.8, 8.8.4.4

---

### Post by carranty on 2012-01-07
> **Dennis N said:**
> I use Google DNS server (its far quicker than my ISP) and enter these values:

8.8.8.8, 8.8.4.4

That's done it!  Thanks, I would never have thought to use those values.

---

### Post by Dennis N on 2012-01-07
Congratulations. Glad you were able to get it working.

---

### Post by imachavel on 2012-01-07
here is mine btw, may not simplify anything, but just for the hell of it:

router i.p. address: 192.168.0.1

subnet mask: 255.255.255.0

dhcp i.p. address range: 192.168.0.100 to 192.168.0.199

mine is a little more simplified. do your settings have password protection? wpa encryption? anything?

---

### Post by carranty on 2012-01-07
> **imachavel said:**
> mine is a little more simplified. do your settings have password protection? wpa encryption? anything?

I use WPA with an eight character alphanumeric passphrase.  I'd recommend using WPA, I'm not sure what its like in the states, but here in the UK the owner of the router is responsible for the actions of whoever uses it (even if they hack into it without permission) so yeah, I like to know its secure!

EDIT: I used to have a much longer passphrase, but it was a pain to reenter every time I flashed my phones ROM or reinstalled an OS.  I found this article interesting, which suggests an 8 character passphrase is more than enough (and is easily memorable).

---

### Post by Dennis N on 2012-01-07
I don't use a static IP address for wireless, just my (Desktop) wired connections. My laptop just uses a DHCP assigned address (but I do specify Google DNS with that also). The laptop wireless connection is encripted.

BTW, using DHCP with a user-specified DNS server requires you use the connection method "Automatic (DHCP) addresses only".

---

