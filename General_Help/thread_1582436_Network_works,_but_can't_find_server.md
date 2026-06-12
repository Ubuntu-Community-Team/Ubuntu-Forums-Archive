---
title: "Network works, but can't find server"
date: 2010-09-26
forum: General Help
---

### Post by Tom of Helatrobus on 2010-09-26
My network is working and shows a connection to my wireless connection (connected at 100%), but firefox shows "Problem loading page" when ever I enter a url. So I can't access the internet. Synaptic doesn't work either. When I try to download, I get a warning "Could not doadload all repository indexes - (-5 No address associated with hostname)"

This is a dual boot machine and the internet connection on the windows side works just fine. The connection worked fine with ubuntu 9.10. But since I partitioned the drive and did a fresh install of 10.4 I can not access the internet.

---

### Post by anirudhtomer on 2010-09-26
are you able to ping the addresses directly?
if yes then it means the connection is perfect.

also as u have specified that the error u get is "No address associated with hostname"
that means you don't have the IP of the DNS server in /etc/resolv.conf file so that it can map hostnames to IP or the wrong IP is specified for the DNS server....the worst case the DNS is faulty(very very rare case)

---

### Post by Tom of Helatrobus on 2010-09-26
> **anirudhtomer said:**
> are you able to ping the addresses directly?
if yes then it means the connection is perfect.

also as u have specified that the error u get is "No address associated with hostname"
that means you don't have the IP of the DNS server in /etc/resolv.conf file so that it can map hostnames to IP or the wrong IP is specified for the DNS server....the worst case the DNS is faulty(very very rare case)

When I ping the network address (10.42.43.1 - in my case) it works 100%.

concerning the ip of the dns server - how could I resolve this situation?

---

### Post by btindie on 2010-09-26
From the terminal type *ifconfig*, does it show that you've been given an IP address?
 
Type *route -n*, does it show that you've been given a default gateway address? In the destination column it will be listed as 0.0.0.0, the gateway address is that of your router/wireless access point.
 
Can you *ping* the ip address of your wireless access point?
 
Edit: usually for a home network your dns server will be the same as your gateway. You can test it with *host *[*www.google.co.uk*]("http://www.google.co.uk")* <IP_OF_GATEWAY>. *Also, try to ping 173.194.37.104 which is a Google IP address.

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> From the terminal type *ifconfig*, does it show that you've been given an IP address?
 
Type *route -n*, does it show that you've been given a default gateway address? In the destination column it will be listed as 0.0.0.0, the gateway address is that of your router/wireless access point.
 
Can you *ping* the ip address of your wireless access point?
 
Edit: usually for a home network your dns server will be the same as your gateway. You can test it with *host *[*www.google.co.uk*]("http://www.google.co.uk")* <IP_OF_GATEWAY>*

When I ented route -n, under destination it reads 10.42.43.0 then 169.254.0.0 and under gateway 0.0.0.0 then 0.0.0.0

---

### Post by anirudhtomer on 2010-09-26
that means ur connection is perfect.
this is how the /etc/resolv.conf file looks like
[http://www.faqs.org/docs/securing/chap9sec91.html](http://www.faqs.org/docs/securing/chap9sec91.html)
(sent a link coz I am using someone else's PC having windows only)

so if you know the DNS server IP address ...lets assume 208.164.186.1

then add the line in your /etc/resolv.conf file
nameserver 208.164.186.1

you can have entries for multiple DNS servers in ur resolv.conf file

hope it helps.

edited::
hey I just saw ur IP address 10.42.43.1-------seems u are accessing net via proxy server.
u know what? in my college the DNS server & proxy server for other services (http,ftp etc) are on the same machine and they share the same IP. may be u r having a similar case.
if yes then add the line 
nameserver 10.42.43.1 in the resolv.conf file.
otherwise find out the DNS server IP.

---

### Post by Tom of Helatrobus on 2010-09-26
> **anirudhtomer said:**
> that means ur connection is perfect.
this is how the /etc/resolv.conf file looks like
[http://www.faqs.org/docs/securing/chap9sec91.html](http://www.faqs.org/docs/securing/chap9sec91.html)
(sent a link coz I am using someone else's PC having windows only)

so if you know the DNS server IP address ...lets assume 208.164.186.1

then add the line in your /etc/resolv.conf file
nameserver 208.164.186.1

you can have entries for multiple DNS servers in ur resolv.conf file

hope it helps.

thomas@thomas-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:e0:dc:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:469396 (469.3 KB)  TX bytes:469396 (469.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:5f:f0:9e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe5f:f09e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26223 (26.2 KB)

thomas@thomas-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
thomas@thomas-laptop:~$

---

### Post by Tom of Helatrobus on 2010-09-26
> **anirudhtomer said:**
> that means ur connection is perfect.
this is how the /etc/resolv.conf file looks like
[http://www.faqs.org/docs/securing/chap9sec91.html](http://www.faqs.org/docs/securing/chap9sec91.html)
(sent a link coz I am using someone else's PC having windows only)

so if you know the DNS server IP address ...lets assume 208.164.186.1

then add the line in your /etc/resolv.conf file
nameserver 208.164.186.1

you can have entries for multiple DNS servers in ur resolv.conf file

hope it helps.

In the resolv.conf file it reads only: 

#Generated by NetworkManager 

(the rest is blank)

Where to I find the DNS server IP address?

---

### Post by btindie on 2010-09-26
Are you able to ping the Google IP address I gave?
 
I don't think it's picked up a default gateway for some reason. It looks like you have the network address and the IPv4LL address. It should look something like this
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.255.255.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
0.0.0.0         **10.255.255.1**    0.0.0.0         UG    0      0        0 eth0

The default gateway being in bold, note the 0.0.0.0's either side.
 
Have you configured if for DHCP or have you given it a static address?

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> Are you able to ping the Google IP address I gave?
 
I don't think it's picked up a default gateway for some reason. It looks like you have the network address and the IPv4LL address. It should look something like this
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.255.255.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
0.0.0.0         **10.255.255.1**    0.0.0.0         UG    0      0        0 eth0

The default gateway being in bold, note the 0.0.0.0's either side.
 
Have you configured if for DHCP or have you given it a static address?

I entered and saved the name server 10.42.43.0 in the resolv.conf file without success. what address did you need me to ping? .Otherwise I haven't made any changes to the configuration DHCP or otherwise

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> wlan0 Link encap:Ethernet HWaddr 00:26:5e:5f:f0:9e 
inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0
You've got an IP address from somewhere and it's not an IPv4LL assigned one. 
 
> **Tom of Helatrobus said:**
>  thomas@thomas-laptop:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.42.43.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan0
You haven't got a default gateway address so won't be able to access the internet.
 
Is the IP address you've got the same/similar to when you boot in Windows?

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> I entered and saved the name server 10.42.43.0 in the resolv.conf file without success. what address did you need me to ping?
 
That's your network address, not the DNS server address so that won't work. Plus there's no default gateway configured so you won't be able to ping it anyhow.
 
The address was 173.194.37.104 which is a Google IP address.
 
Can you disconnect your wireless connection then try connecting again..

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> That's your network address, not the DNS server address so that won't work. Plus there's no default gateway configured so you won't be able to ping it anyhow.
 
The address was 173.194.37.104 which is a Google IP address.
 
Can you disconnect your wireless connection then try connecting again..

The ping at that address was unsuccessful. I will try to disconnect and reconnect. The reconnection didn't work.

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> You've got an IP address from somewhere and it's not an IPv4LL assigned one. 
 

You haven't got a default gateway address so won't be able to access the internet.
 
Is the IP address you've got the same/similar to when you boot in Windows?

how do I find the address which I use to boot in windows?

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> how do I find the address which I use to boot in windows?
 
From a command prompt type *ipconfig /all.* If you can post all the output for your Wireless Network Connection.
 
Try restarting the network *sudo stop networking* / *sudo start networking.*
Then if that doesn't work you may want to try deleting your wireless profile and recreating it.

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> From a command prompt type *ipconfig /all.* If you can post all the output for your Wireless Network Connection.
 
Try restarting the network *sudo stop networking* / *sudo start networking.*
Then if that doesn't work you may want to try deleting your wireless profile and recreating it.

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Thomas>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Thomas-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : chn.comcast.net

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : chn.comcast.net
   Description . . . . . . . . . . . : Broadcom 802.11b/g WLAN
   Physical Address. . . . . . . . . : C4-17-FE-C0-DB-F3
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b937:fc26:9897:bdf0%13(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.5(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, September 26, 2010 9:50:40 AM
   Lease Expires . . . . . . . . . . : Sunday, September 26, 2010 12:20:45 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 331618302
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-13-17-0A-45-C8-0A-A9-1C-AD-F7

   DNS Servers . . . . . . . . . . . : 68.87.85.98
                                       68.87.69.146
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.chn.comcast.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : chn.comcast.net
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 12:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e74:2415:2d82:3f57:fffa(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::2415:2d82:3f57:fffa%14(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Users\Thomas>


-----------------------------------------
Tried stopping and restarting networking, but it didn't work.

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> 
Wireless LAN adapter Wireless Network Connection:
 
Connection-specific DNS Suffix . : chn.comcast.net
Description . . . . . . . . . . . : Broadcom 802.11b/g WLAN
Physical Address. . . . . . . . . : C4-17-FE-C0-DB-F3
DHCP Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
Link-local IPv6 Address . . . . . : fe80::b937:fc26:9897:bdf0%13(Preferred)
IPv4 Address. . . . . . . . . . . : 192.168.0.5(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Lease Obtained. . . . . . . . . . : Sunday, September 26, 2010 9:50:40 AM
Lease Expires . . . . . . . . . . : Sunday, September 26, 2010 12:20:45 PM
Default Gateway . . . . . . . . . : 192.168.0.1
DHCP Server . . . . . . . . . . . : 192.168.0.1
DHCPv6 IAID . . . . . . . . . . . : 331618302
DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-13-17-0A-45-C8-0A-A9-1C-AD-F7
 
DNS Servers . . . . . . . . . . . : 68.87.85.98
68.87.69.146
NetBIOS over Tcpip. . . . . . . . : Enabled
 
Ok, so the IP address you're getting is 192.168.0.5, default gateway is 192.168.0.1 and DNS servers 68.87.85.98 & 68.87.69.146.
 
I'm not sure where your Lucid install is getting the 10.x.x.x address from.
 
Try deleting your Wireless profile and recreating it. Use *ifconfig wlan0* to see if you've got a suitable IP address and *iwconfig wlan0* to see if you're connected to the correct wireless access point. It is connected to the correct SSID?

---

### Post by Tom of Helatrobus on 2010-09-26
thomas@thomas-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:5e:5f:f0:9e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe5f:f09e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:30627 (30.6 KB)

thomas@thomas-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:97:D9:7C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thomas@thomas-laptop:~$

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> Ok, so the IP address you're getting is 192.168.0.5, default gateway is 192.168.0.1 and DNS servers 68.87.85.98 & 68.87.69.146.
 
I'm not sure where your Lucid install is getting the 10.x.x.x address from.
 
Try deleting your Wireless profile and recreating it. Use *ifconfig wlan0* to see if you've got a suitable IP address and *iwconfig wlan0* to see if you're connected to the correct wireless access point. It is connected to the correct SSID?

how do I find the wireless profile in order to delete it? I assume it will recreate itself...

---

### Post by btindie on 2010-09-26
You're still getting that 10.42.43.1 address, any idea where that could be coming from? Have you configured a static address on there before??
It's saying the wireless access point you're connected to is called HomeNetwork, is that correct?
 
Not sure if this will work but no harm trying. If you do
```
ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up
ping 192.168.0.1
```
Does that return a response?
To reverse the affects of that do
```
ifconfig wlan0:1 0.0.0.0 netmask 0.0.0.0
ifconfig wlan0:1 down
```
 
Have you tried removing the profile and adding it back?

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> how do I find the wireless profile in order to delete it? I assume it will recreate itself...
 
Up the top right hand corner you'll have the network icon, click on that and it should give you the option to edit your profiles. Delete your profile then close the profile editor. Click on the network icon again and it'll give a list of available access points, click the one you want and it'll give you the option to configure it. The default setting should be fine, you'll just need to enter your WEP/WPA(2) key.

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> You're still getting that 10.42.43.1 address, any idea where that could be coming from? Have you configured a static address on there before??
It's saying the wireless access point you're connected to is called HomeNetwork, is that correct?
 
Not sure if this will work but no harm trying. If you do
```
ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up
ping 192.168.0.1
```Does that return a response?
To reverse the affects of that do
```
ifconfig wlan0:1 0.0.0.0 netmask 0.0.0.0
ifconfig wlan0:1 down
```Have you tried removing the profile and adding it back?

thomas@thomas-laptop:~$ ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up ping 192.168.0.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFFLAGS: Permission denied
ping: Unknown host
ifconfig: `--help' gives usage information.
thomas@thomas-laptop:~$ ifconfig wlan0:1 0.0.0.0 netmask 0.0.0.0 ifconfig wlan 0:1 down
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
ifconfig: Unknown host
ifconfig: `--help' gives usage information.
thomas@thomas-laptop:~$ 

-------------------------------------------------

I don't know how to remove the profile...

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> thomas@thomas-laptop:~$ ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up ping 192.168.0.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFFLAGS: Permission denied
ping: Unknown host
ifconfig: `--help' gives usage information.
thomas@thomas-laptop:~$ ifconfig wlan0:1 0.0.0.0 netmask 0.0.0.0 ifconfig wlan 0:1 down
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
ifconfig: Unknown host
ifconfig: `--help' gives usage information.
thomas@thomas-laptop:~$ 
 
-------------------------------------------------
 
I don't know how to remove the profile...
 
They're two seperate commands... You'll also need to prefix ifconfig with *sudo*
```
sudo ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up
ping 192.168.0.1
```
When you do the ping command does it get a response?
 
Run the network-admin GUI, (System)->(Administration)->(Networking) to recreate the wireless profile. See [Using network-admin, the GUI Network Tool]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> They're two seperate commands... You'll also need to prefix ifconfig with *sudo*
```
sudo ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up
ping 192.168.0.1
```When you do the ping command does it get a response?
 
Run the network-admin GUI, (System)->(Administration)->(Networking) to recreate the wireless profile. See [Using network-admin, the GUI Network Tool]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

thomas@thomas-laptop:~$ sudo ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up
[sudo] password for thomas: 
thomas@thomas-laptop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.5 icmp_seq=1 Destination Host Unreachable
From 192.168.0.5 icmp_seq=2 Destination Host Unreachable
From 192.168.0.5 icmp_seq=3 Destination Host Unreachable
From 192.168.0.5 icmp_seq=4 Destination Host Unreachable
From 192.168.0.5 icmp_seq=5 Destination Host Unreachable
From 192.168.0.5 icmp_seq=6 Destination Host Unreachable
From 192.168.0.5 icmp_seq=7 Destination Host Unreachable
From 192.168.0.5 icmp_seq=8 Destination Host Unreachable
From 192.168.0.5 icmp_seq=9 Destination Host Unreachable

---

### Post by Tom of Helatrobus on 2010-09-26
> **btindie said:**
> They're two seperate commands... You'll also need to prefix ifconfig with *sudo*
```
sudo ifconfig wlan0:1 192.168.0.5 netmask 255.255.255.0 up
ping 192.168.0.1
```When you do the ping command does it get a response?
 
Run the network-admin GUI, (System)->(Administration)->(Networking) to recreate the wireless profile. See [Using network-admin, the GUI Network Tool]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")


I see System> Administration > Network Tools but not System > Administration > Networking, maybe this is new to 10.4.

went to system > preferences > network connections, selected the wireless tab, selected my network and pressed delete. then network icon on the top right (next to the volume) and reconnected to my network and IT WORKED!!!

---

### Post by Tom of Helatrobus on 2010-09-26
Thanks for all the help. I have no idea how the problem arose in the first place. But it seems that deleting and resetting the network connection did the trick. Thanks a million for all the help - how do I learn more about this stuff?

---

### Post by btindie on 2010-09-26
Not sure what it's called under Lucid, but there should be a Network icon in the top right corner which will all you to configure networking, I don't think it's that dissimilar to Karamic. Failing that, type NetworkManager in at the terminal
 
Not sure if this is of any relevance [http://www.qc4blog.com/?p=857](http://www.qc4blog.com/?p=857)

---

### Post by Tom of Helatrobus on 2010-09-26
this is what the new configurations look like: 

thomas@thomas-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:e0:dc:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65680 (65.6 KB)  TX bytes:65680 (65.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:5f:f0:9e  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe5f:f09e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:233094 (233.0 KB)  TX bytes:43949 (43.9 KB)

thomas@thomas-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:97:D9:7C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thomas@thomas-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
thomas@thomas-laptop:~$

---

### Post by btindie on 2010-09-26
> **Tom of Helatrobus said:**
> Thanks for all the help. I have no idea how the problem arose in the first place. But it seems that deleting and resetting the network connection did the trick. Thanks a million for all the help - how do I learn more about this stuff?
 
Pleased to hear you finally got your problem sorted!
 
Nothing more than a lot of reading and experimenting, be prepared to do quite a lot of fixing, but that's how you learn! Take a look at the docs for Lucid [here]("http://ubuntuguide.org/wiki/Ubuntu:Lucid").

---

