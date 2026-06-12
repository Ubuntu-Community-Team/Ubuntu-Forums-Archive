---
title: "help setting up server 10.10 please"
date: 2010-12-29
forum: General Help
---

### Post by Red Kelly on 2010-12-29
[SIZE=2]Hi I have run into a few problems i was wondering if someone could help?

What I'm trying to do:
I'd like to have a Ubuntu server setup so that i can access files from windows 7 and so windows 7 can access files on Ubuntu. I also have myth-TV installed (this is working fine).
I am also about to get a asrock 330 for a HTPC (XBMC-live).
In the future I would like to run the Internet through the server so I can see traffic for other computers and the added security of completely fire walling one connection and allowing the home network to move around a bit.

What the problems are:
Basically i am getting nothing on the network from ether computer. In Ubuntu If i try to view Network > Windows Network I get the error: "Unable to mount location"  "Failed to retrieve share list form server".  
In windows I am unable to see shared folders or the Ubuntu server (I can see the Myth-TV stream)

What I have tried:
I understand Ubuntu uses samba to talk to windows networks, and although I understand this is installed with Ubuntu and meant to work in the background when it didn't work straight up I tried all the samba GUI that are in the software center. Everything seems to be OK with all of them.
smbtree in terminal shows nothing.

What I have got:
I have installed Ubuntu 10.10 64-bit desktop edition on an ASUS M4A78T-E
Using a Telsta router (Wireless to Windows) for network and Internet (Internet works fine on both).

Oddity: 
In Network Connections Auto eth0 is listed as never used even tho that is the connection I am using.

If anyone could point me in the right direction I would greatly appreciated it. 
(Also, can anyone see any potential problems with the HTPC, fingered it is based on Ubuntu so shouldn't be a problem.)
[/SIZE]

---

### Post by Red Kelly on 2010-12-29
[SIZE=2]Just installed Ubuntu 10.10 on laptop (duel boot) and I have more problems.
I thought I'd try Ubuntu on the laptop because I figured it would be easier for Ubuntu to talk to Ubuntu than Ubuntu to windows, but alas i have come against more problems.
The laptop (Samsung R780-JS02AU) installed fine it showed internet connection with a green tick when installing. Now I cant access the internet on it. Both wired and wireless connections show they are connected (eth0 is also shown as never used).
When I try sudo /etc/init.d/networking restart
I get
```
*  Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0
Ignoring unknown interface wlan0=wlan0
Ignoring unknown interface eth0=eth0

```
Is this right?
[/SIZE][SIZE=2]I can ping between the two.


[/SIZE]

---

### Post by Red Kelly on 2010-12-29
[SIZE=2]Ok i found [http://library.gnome.org/users/shares-admin/stable/tool-getting-started.html.en](http://library.gnome.org/users/shares-admin/stable/tool-getting-started.html.en) 
On the server I tried the command line: shares-admin (as System>Administration>Shares isn't there)
It Prompted me to Install "Unix network support (NFS)" and "Windows network support (SMB)"
I thought this was a bit strange as shouldn't these be installed by default?
I clicked OK to install and they downloaded and installed then up pops the window again, saying I need to install the support for (NFS) and (SMB). If I click Install services it just reappears. I click cancel and it disappears. 
The Shared folders listed are:
/home/netlogon
/var/samba/profiles
/home/pdf-documents
I added /media/MULTIMEDIA (my hard drive for movies music and stuff)
(don't expect adding any will change anything but maybe it wont get reset when i restart the computer)
Nothing has changed as far as I can tell.
[/SIZE]

---

### Post by Bucky Ball on 2010-12-29
You really should be using an LTS release for a server (long term support).

I would suggest 10.04. Five years support.

---

### Post by Red Kelly on 2010-12-29
Arrr why is this so hard!!

---

### Post by Red Kelly on 2010-12-29
It wont be only a server. Anyway will 10.04 change anything much?

---

### Post by Bucky Ball on 2010-12-29
When you've figured it out it'll be easy and your server will stay up until you do something to kill it. Probably worth the effort in that case. A zillion times more preferable to the leaking bucket that is a Windows server.

---

### Post by Red Kelly on 2010-12-30
going to try a reinstall I've changed to many settings to be shore that nothing is conflicting.

---

### Post by Bucky Ball on 2010-12-30
Go 10.04 LTS. Better option for server as mentioned. ;)

---

### Post by Red Kelly on 2010-12-30
Things seem to be getting worse after the install. Now I don't seem to have internet connection, or do I? I can't seem to find anything wrong. But firefox wont load any pages, just sits on "waiting for www.google.com..."
And if I try to update with Update manager it says downloading Release.gpg and downloaded 65B of 65B under Details it shows all 100%. After hanging on that for about 4 min it jumps to Downloaded 659B of 659B and the orange bar moves back and forth behind it it has stayed like that for the last hour and a half or more.

My laptop when loaded into windows 7 still has a fine connection to the internet.

I have tryed some commands I found in old forums and posts but I don't really know what I'm looking for. 
This is what i got:
```

luke-server@server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         BigPond.BigPond 0.0.0.0         UG    0      0        0 eth0
luke-server@server:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
luke-server@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:82:f7:2f  
          inet addr:10.0.0.34  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe82:f72f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1805 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:7762717 (7.7 MB)  TX bytes:300944 (300.9 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

luke-server@server:~$ ping -c 4 google.com
PING google.com (66.102.11.104) 56(84) bytes of data.
64 bytes from syd01s01-in-f104.1e100.net (66.102.11.104): icmp_req=1 ttl=52 time=52.2 ms
64 bytes from syd01s01-in-f104.1e100.net (66.102.11.104): icmp_req=2 ttl=52 time=50.7 ms
64 bytes from syd01s01-in-f104.1e100.net (66.102.11.104): icmp_req=3 ttl=52 time=51.4 ms
64 bytes from syd01s01-in-f104.1e100.net (66.102.11.104): icmp_req=4 ttl=52 time=51.3 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 50.777/51.435/52.221/0.563 ms
luke-server@server:~$ 

```

I am running out of places to look for answers.
So please help I just need to be pointed in the right direction. Where can I find information for this?

---

