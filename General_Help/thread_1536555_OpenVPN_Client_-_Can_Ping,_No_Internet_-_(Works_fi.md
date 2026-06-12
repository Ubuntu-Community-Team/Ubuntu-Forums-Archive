---
title: "OpenVPN Client - Can Ping, No Internet - (Works fine with Windows OpenVPN Client)"
date: 2010-07-22
forum: General Help
---

### Post by Trident911 on 2010-07-22
I come to you at the end of my tether, been at this all day haha. Recently setup a OpenVPN server on my Windows Server 2008 R2 box and a client on Windows 7 (Both x64) - it has been going swimmingly well.

However tonight, I decided to reformat an old PC laying around and give Lucid (Desktop 64bit) within *Virtual Box *- everything's been going great (and fast!). However, then came the part where I needed to setup OpenVPN on my Ubuntu Lucid (Client) to connect to my W2K8 R2 (Server). 

I firstly installed *OpenVPN* from the source tar.gz - and then went ahead and followed this great guide on setting up *GOopenVPN *([http://tranceparance.wordpress.com/2009/02/28/gopenvpn-installation-instructions-for-ubuntu-linux-810/](http://tranceparance.wordpress.com/2009/02/28/gopenvpn-installation-instructions-for-ubuntu-linux-810/)) - again, everything is going fine.

I copied the appropriate .key, .crt's and my client.conf across (Listed below are both the *Server *and *Client *configs):

[B]Server Config:

[/B]> local xxx.xxx.xxx.xxx
port 1194
proto udp
mssfix 1400
push "dhcp-option DNS xxx.xxx.xxx.xxx"
push "dhcp-option DNS xxx.xxx.xxx.xxx"
dev tap
ca "ca.crt"  
cert "Server.crt"
key "Server.key"
dh "dh1024.pem"
server 192.168.10.0 255.255.255.128 
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1"
keepalive 10 120
cipher BF-CBC
comp-lzo
max-clients 5
persist-key
persist-tun
status openvpn-status.log
verb 3[B]Client Config:

[/B]> client
proto udp
dev tap
remote xxx.xxx.xxx.xxx 1194
resolv-retry infinite
nobind
persist-key
persist-tun
cipher BF-CBC
ca ca.crt
cert client.crt
key client.key
comp-lzo
verb 3
Now as I've stated, everything is connecting **beautifully**, I can ping the Server's *internal *and *external *IP, and the Server can ping the Client's *internal *IP. **HOWEVER** as soon as I try to access _external_ traffic - aka the Internet in general - through Browsers/Pings in terminal I promptly receive a kick to the _**balls**_.

The **weird **thing is this works _PERFECTLY_ under both Windows machines - so the Server's NAT'ing to me seems fine (it originally proved a problem until I setup *Routing and Remote Access *on the W2K8 machine). 

[COLOR=Red]I'm thinking it might have something to do with my running Ubuntu in *Virtual Box* (?) and the way it sets up its connections to my Windows 7 host.. **OR **routing between *eth0 *and the *tap *device... But I'm at a loss - any help would be GREATLY appreciated.[/COLOR]

[B]
EDIT1: [/B]For good measure, he is my *Client *log (on Verb 3) -

> Thu Jul 22 16:47:27 2010: MANAGEMENT: CMD 'state on'

Thu Jul 22 16:47:27 2010: MANAGEMENT: CMD 'auth-retry interact'

Thu Jul 22 16:47:27 2010: MANAGEMENT: CMD 'hold release'

Thu Jul 22 16:47:27 2010: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.

Thu Jul 22 16:47:27 2010: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts

Thu Jul 22 16:47:27 2010: WARNING: file 'client.key' is group or others accessible

Thu Jul 22 16:47:27 2010: LZO compression initialized

Thu Jul 22 16:47:27 2010: Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]

Thu Jul 22 16:47:27 2010: Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]

Thu Jul 22 16:47:27 2010: Local Options hash (VER=V4): 'd79ca330'

Thu Jul 22 16:47:27 2010: Expected Remote Options hash (VER=V4): 'f7df56b8'

Thu Jul 22 16:47:27 2010: Socket Buffers: R=[124928->131072] S=[124928->131072]

Thu Jul 22 16:47:27 2010: UDPv4 link local: [undef]

Thu Jul 22 16:47:27 2010: UDPv4 link remote: **<Public IP of Server>**:1194

Thu Jul 22 16:47:27 2010: MANAGEMENT: >STATE:1279810047,WAIT,,,

Thu Jul 22 16:47:28 2010: MANAGEMENT: >STATE:1279810048,AUTH,,,

Thu Jul 22 16:47:28 2010: TLS: Initial packet from **<Public IP of Server>**:1194, sid=df845327 c7f6a6d5

Thu Jul 22 16:47:29 2010: VERIFY OK: depth=1, /C=DK/ST=NA/L=**BLAH**/O=**BLAH**/CN=**BLAH**/emailAddress=**BLAH**

Thu Jul 22 16:47:29 2010: VERIFY OK: depth=0, /C=DK/ST=NA/O=**BLAH**/CN=**BLAH**/emailAddress=**BLAH**

Thu Jul 22 16:47:33 2010: Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key

Thu Jul 22 16:47:33 2010: Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication

Thu Jul 22 16:47:33 2010: Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key

Thu Jul 22 16:47:33 2010: Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication

Thu Jul 22 16:47:33 2010: Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA

Thu Jul 22 16:47:33 2010: [Sensor-Server] Peer Connection Initiated with **<Public IP of Server>**:1194

Thu Jul 22 16:47:34 2010: MANAGEMENT: >STATE:1279810054,GET_CONFIG,,,

Thu Jul 22 16:47:35 2010: SENT CONTROL [Sensor-Server]: 'PUSH_REQUEST' (status=1)

Thu Jul 22 16:47:35 2010: PUSH: Received control message: 'PUSH_REPLY,dhcp-option DNS **<DNS IP 1>**,dhcp-option DNS **<DNS IP 2>**,redirect-gateway def1,route-gateway 192.168.10.1,ping 10,ping-restart 120,ifconfig 192.168.10.4 255.255.255.128'

Thu Jul 22 16:47:35 2010: OPTIONS IMPORT: timers and/or timeouts modified

Thu Jul 22 16:47:35 2010: OPTIONS IMPORT: --ifconfig/up options modified

Thu Jul 22 16:47:35 2010: OPTIONS IMPORT: route options modified

Thu Jul 22 16:47:35 2010: OPTIONS IMPORT: route-related options modified

Thu Jul 22 16:47:35 2010: OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified

Thu Jul 22 16:47:35 2010: ROUTE default_gateway=10.0.2.2

Thu Jul 22 16:47:35 2010: TUN/TAP device tap0 opened

Thu Jul 22 16:47:35 2010: TUN/TAP TX queue length set to 100

Thu Jul 22 16:47:35 2010: MANAGEMENT: >STATE:1279810055,ASSIGN_IP,,192.168.10.4,

Thu Jul 22 16:47:35 2010: /sbin/ifconfig tap0 192.168.10.4 netmask 255.255.255.128 mtu 1500 broadcast 192.168.10.127

Thu Jul 22 16:47:36 2010: /sbin/route add -net **<Public IP of Server>** netmask 255.255.255.255 gw 10.0.2.2

Thu Jul 22 16:47:36 2010: /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 192.168.10.1

Thu Jul 22 16:47:36 2010: /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 192.168.10.1

Thu Jul 22 16:47:36 2010: Initialization Sequence Completed

Thu Jul 22 16:47:36 2010: MANAGEMENT: >STATE:1279810056,CONNECTED,SUCCESS,192.168.10.4,**<Public IP of Server>**

and an **ifconfig** on *Client*:

> eth0      Link encap:Ethernet  HWaddr 08:00:27:c6:9e:7a  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fec6:9e7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60980161 (60.9 MB)  TX bytes:11642615 (11.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122018 (122.0 KB)  TX bytes:122018 (122.0 KB)

tap0      Link encap:Ethernet  HWaddr 36:cb:90:e6:28:25  
          inet addr:192.168.10.4  Bcast:192.168.10.127  Mask:255.255.255.128
          inet6 addr: fe80::34cb:90ff:fee6:2825/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1086 (1.0 KB)  TX bytes:4136 (4.1 KB)


---

### Post by Trident911 on 2010-07-22
*Shameless bump :(*

---

### Post by The Cog on 2010-07-22
I wonder if it's just a DNS issue. Can you ping internet addresses by IP address? if you try to ping internet sites by name, does it say unknown host or does it resolve the address and then timeout? "a kick in the balls" isn't very informative, and probably not true.

The output of these might help:
route -n
cat /etc/resolv.conf
tracepath ubuntuforums.com
tracepath 91.189.94.186

---

### Post by Trident911 on 2010-07-22
Problem solved - after having a nights rest and ready to smash my head at it again today, I came across another blog site that suggested a *slightly* different **Client.Conf**:

> client
dev tap
proto udp
remote xxx.xxx.xxx.xxx 1194
ping 10
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
ns-cert-type server
comp-lzo
pull
verb 3

Now don't ask me how - but the combination of **pull**, **ns-cert-type server** or **ping 10**, _**FIXED IT!**_

**[COLOR="Red"]Please read reply below - the above WORKED until I used the Update Manager..[/COLOR]**

---

### Post by Trident911 on 2010-07-23
I spoke to soon :( - It was working **PRIOR** to using the Update Manager to update my machine :confused:

The output you requested (It seems theres a DNS issue):

**_route -n_**

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.128 U     0      0        0 tap0
192.168.10.0    0.0.0.0         255.255.255.128 U     0      0        0 tap1
192.168.231.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.10.1    128.0.0.0       UG    0      0        0 tap0
128.0.0.0       192.168.10.1    128.0.0.0       UG    0      0        0 tap0
0.0.0.0         192.168.231.2   0.0.0.0         UG    0      0        0 eth0

**_cat /etc/resolv.conf_**

> # Generated by NetworkManager
domain localdomain
search localdomain
nameserver 192.168.231.2


**_tracepath ubuntuforums.com_**

>  1:  ubuntu.local (192.168.10.4)                            0.106ms pmtu 1500
 1:  ubuntu.local (192.168.10.4)                          351.905ms !H
 1:  no reply
 1:  ubuntu.local (192.168.10.4)                          1003.088ms !H
     Resume: pmtu 1500 


**_tracepath 91.189.94.186_**

>  1:  ubuntu.local (192.168.10.4)                            0.075ms pmtu 1500
 1:  ubuntu.local (192.168.10.4)                          509.164ms !H
 1:  no reply
 1:  ubuntu.local (192.168.10.4)                          1004.383ms !H
     Resume: pmtu 1500 


**EDIT1:**

[COLOR="Red"]AHUH! It seems that whenever I restart my Ubuntu its re-creating the **Tap0** device, which is doubling up and coursing the problem when I go to connect on a fresh reboot - 2 devices are then present - **Tap0** and **Tap1**. If I manually remove **Tap0** (so only **Tap1**), everything is fine :confused:

If I edit **dev tap0** into the *Client.conf* instead of my **dev tap** it throws the following error:

> Thu Jul 22 21:54:48 2010: Note: Cannot ioctl TUNSETIFF tap0: Device or resource busy (errno=16)

Thu Jul 22 21:54:48 2010: Note: Attempting fallback to kernel 2.2 TUN/TAP interface

Thu Jul 22 21:54:48 2010: Cannot open TUN/TAP dev /dev/tap0: No such file or directory (errno=2)

I can't for the life of me **STOP** Tap0 being re-created on startup no matter what I do.[/COLOR]

---

### Post by The Cog on 2010-07-23
That extra tap is odd. I can't really say anything about that though - I've only ever used OpenVPN in tun mode, and I don't see an extra tun being generated.

It might be worth trying to set something like **dev tap99** in the config file and see if that helps. Also see if tap0 is created even before you start OpenVPN - something else might be making it. I wonder if it's an artifact of running inside virtualbox though I don't really see why it should be. tap0 and tap1 seem to have the same IP address.

---

### Post by Trident911 on 2010-07-23
> **The Cog said:**
> That extra tap is odd. I can't really say anything about that though - I've only ever used OpenVPN in tun mode, and I don't see an extra tun being generated.

It might be worth trying to set something like **dev tap99** in the config file and see if that helps. Also see if tap0 is created even before you start OpenVPN - something else might be making it. I wonder if it's an artifact of running inside virtualbox though I don't really see why it should be. tap0 and tap1 seem to have the same IP address.

Do more research on the matter last night Cog, it seems that OpenVPN is creating the Tap0 device on reboot - and as such, is already connected upon startup (aka checking with 'What is my IP' type sites).

This is indeed weird though, because I have not set it up to do so, but basically I can understand what is going on now/why both have the same IP.

When I go to start goOpenVPN (GUI Frontend), it is creating a **NEW** Tap device, not realizing that OpenVPN (cmd line) has already setup the device/connection, and as a result doubling up.

In a perfect world - and what I THINK should be happening is that OpenVPN should be starting up and creating a Connection off the bat - I want it to only do so when I start it from the GUI.. Not sure how to go about doing this, NOR do I know why OpenVPN has just gone off and done this.

**Further Testing:**

Simply re-installing OpenVPN (apt-get remove openvpn, then apt-get install openvpn) _doesn't_ fix the issue - upon reboot the device is still there (aka configs are left over somewhere).

If I however use; *apt-get purge openvpn* than re-install it (ensuring /etc/openvpn is no longer there before the reboot) - the Tap0 device isn't present.

But upon the FIRST running of *goOpenVPN* is where it gets weird - I start goOpenVPN, connect - everything is lovely. However when I disconnect, close goOpenVPN and rebooot (goOpenVPN is not added to Session Startup or anything) and do an *ifconfig* on reboot - Tap0 is there! It seems OpenVPN decides to just **takeover** and start the connection on startup here on out...

Now I'm completly lost as to **WHY** this is.. and would love for someone to explain.

---

### Post by The Cog on 2010-07-24
I know the answer to that - or, I think I do. When you install OpenVPN, it gets set to run as a daemon at startup. And when it starts, it looks for any configuration files in /etc/openvpn and it starts those VPNs up. 

Perhaps the best way to prevent this is to edit /etc/default/openvpn and un-comment the line "AUTOSTART="none". Then you should be able to start and stop the VPN on demand with **sudo /etc/init.d/openvpn start client** where client is the name of the config file in /etc/openvpn. And of course, **sudo /etc/init.d/openvpn stop client**.

---

### Post by MarlonBlack on 2010-07-24
Hi Mate

I think the problem is with DNS . Try to ping internet address. I think the isuue would be solved.

---

### Post by The Cog on 2010-07-24
> **MarlonBlack said:**
> Hi Mate

I think the problem is with DNS . Try to ping internet address. I think the isuue would be solved.

I don't think it's a DNS issue. When he tries to trace to ubuntuforums.com, it tries. If DNS wasn't working, tracepath would have said unknown host. The fact that it has started listing a path means that it was able to resolve ubuntuforums.com into an IP address to trace to, so DNS worked. Tracepath to ubuntuforums.com by both name and by IP address give identical results.

I originally thought it was a DNS issue though, and I asked for those trace commands to collect proof of that.

---

### Post by Trident911 on 2010-07-26
> **The Cog said:**
> I don't think it's a DNS issue. When he tries to trace to ubuntuforums.com, it tries. If DNS wasn't working, tracepath would have said unknown host. The fact that it has started listing a path means that it was able to resolve ubuntuforums.com into an IP address to trace to, so DNS worked. Tracepath to ubuntuforums.com by both name and by IP address give identical results.

I originally thought it was a DNS issue though, and I asked for those trace commands to collect proof of that.

Alright Cog, thanks for ALL your help mate - your advice about removing the **AUTOSTART **line worked!

HOWEVER, I have even something weirder now >< - I went ahead and rebuilt my Ubuntu Virtualbox environment so I could follow the instructions of the guides I linked above plus your advice from a fresh base.

Now for the life of me I'm back to square one haha - OpenVPN is connecting successfully to server but NO external internet, here are the request things you asked for the first time around:

**_route -n_**:

> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**<Servers' IP>** 10.0.2.2        255.255.255.255 UGH   0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.128 U     0      0        0 tap0
10.0.2.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.10.1    128.0.0.0       UG    0      0        0 tap0
128.0.0.0       192.168.10.1    128.0.0.0       UG    0      0        0 tap0
0.0.0.0         10.0.2.2        0.0.0.0         UG    0      0        0 eth0



**_cat /etc/resolv.conf_**:

> # Generated by NetworkManager
nameserver 192.168.1.254



[B][U]tracepath ubuntuforums.com:

[/U][/B]> gethostbyname2: Unknown host

The thing that I can't figure out is WHY has my routing and resolv.conf CHANGED using the exact same client.conf as I was previously.. somethings gone wrong :(

---

### Post by Trident911 on 2010-07-27
Went ahead and figured I would try ANOTHER OS under Virtualbox just incase this was a recurring act of God. It seems it might be..

[http://forums.virtualbox.org/viewtopic.php?f=3&t=33217](http://forums.virtualbox.org/viewtopic.php?f=3&t=33217)

I've posted over there with some updated information if you wanted to have a look **Cog**.

Basically; installed Fedora 13 and the same thing is happening, I can ping Server Public/Internal IPs, but nothing else is being resolved when coming from outside the VPN. I even went to the extent of manually editing the missing entries into */etc/resolv.conf *with no luck.

Again - all works perfect on my Windows machine (non-Virtualbox/VMware)...

---

### Post by ethnochemist on 2010-08-04
EDIT: Problem solved. The nameserver (192.168.1.1) wasn't in resolv.conf. I just now need to figure out how to have openvpn automatically add it in.

I'm having the exact same problem as above. Everything works except DNS. 

The saddest part is that it worked at some point. And I have no idea what I changed. It seemed like fixing the DNS would be such a simple issue; I've checked everything in my conf files and everything checks out.

Any ideas would be great; I'm completely out.

Thanks!

---

### Post by Blackyell on 2011-04-04
Hello,

I know this thread is a little old, but I have the same problem than ethnochemist.

All is working fine except DNS.

I can ping local/external IP without any problem, but can't ping with hostname.

If I edit /etc/resolv.conf manually, to add Google DNS IP, it works.

Why OpenVPN is not configuring correctly that ?

Thank you

---

