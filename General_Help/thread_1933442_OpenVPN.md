---
title: "OpenVPN"
date: 2012-02-29
forum: General Help
---

### Post by carranty on 2012-02-29
I've just purchased a subscription to StrongVPN's OpenVPN service and am trying to get it to work on my Ubuntu 10.04 machine but can't.  I've installed the network-manager-openvpn and openvpn packages and configured the vpn (this is easily done, all I did was point network manager to the configuration file and it fills everything in automatically).

However when I try to connect I get the error message

"The VPN connection failed because there were no valid vpn secrets".

Anyone had any success getting such a connection to work in Ubuntu?

---

### Post by raja.genupula on 2012-02-29
Hi please restart your network manager 
```
sudo /etc/init.d/network-manager restart
```

and try again , let us know what you got .

all the best.

---

### Post by carranty on 2012-02-29
This gives a different error message of 

"The VPN connection failed because the connection attempt timed out"

---

### Post by raja.genupula on 2012-02-29
Give a restart to your system now and try again to connect .

---

### Post by carranty on 2012-02-29
> **raja.genupula said:**
> Give a restart to your system now and try again to connect .

Same as above, connection times out.

---

### Post by carranty on 2012-03-02
Anyone?

---

### Post by raja.genupula on 2012-03-02
Hi look at this
[https://forum.perfect-privacy.com/showthread.php?t=934](https://forum.perfect-privacy.com/showthread.php?t=934)

---

### Post by carranty on 2012-03-02
> **raja.genupula said:**
> Hi look at this
[https://forum.perfect-privacy.com/showthread.php?t=934](https://forum.perfect-privacy.com/showthread.php?t=934)

Still no joy, 

```
birbeth@birbeth-desktop:~$ sudo openvpn --cd StrongVPN/ --config ovpn107.ovpn
[sudo] password for birbeth: 
Fri Mar  2 10:05:23 2012 us=776284 Current Parameter Settings:
Fri Mar  2 10:05:23 2012 us=776356   config = 'ovpn107.ovpn'
Fri Mar  2 10:05:23 2012 us=776369   mode = 0
Fri Mar  2 10:05:23 2012 us=776379   persist_config = DISABLED
Fri Mar  2 10:05:23 2012 us=776390   persist_mode = 1
Fri Mar  2 10:05:23 2012 us=776400 NOTE: --mute triggered...
Fri Mar  2 10:05:23 2012 us=776421 256 variation(s) on previous 5 message(s) suppressed by --mute
Fri Mar  2 10:05:23 2012 us=776434 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Fri Mar  2 10:05:23 2012 us=776516 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Fri Mar  2 10:05:23 2012 us=776529 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Mar  2 10:05:23 2012 us=777258 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Mar  2 10:05:23 2012 us=862623 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Fri Mar  2 10:05:23 2012 us=862668 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Mar  2 10:05:23 2012 us=862680 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Mar  2 10:05:23 2012 us=862713 LZO compression initialized
Fri Mar  2 10:05:23 2012 us=862786 Control Channel MTU parms [ L:1546 D:166 EF:66 EB:0 ET:0 EL:0 ]
Fri Mar  2 10:05:23 2012 us=862854 Data Channel MTU parms [ L:1546 D:1390 EF:46 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Mar  2 10:05:23 2012 us=862866 Fragmentation MTU parms [ L:1546 D:1390 EF:45 EB:135 ET:1 EL:0 AF:3/1 ]
Fri Mar  2 10:05:23 2012 us=862886 Local Options String: 'V4,dev-type tun,link-mtu 1546,tun-mtu 1500,proto UDPv4,comp-lzo,mtu-dynamic,keydir 1,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-client'
Fri Mar  2 10:05:23 2012 us=862897 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1546,tun-mtu 1500,proto UDPv4,comp-lzo,mtu-dynamic,keydir 0,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-server'
Fri Mar  2 10:05:23 2012 us=862919 Local Options hash (VER=V4): '551868c6'
Fri Mar  2 10:05:23 2012 us=862934 Expected Remote Options hash (VER=V4): 'e34c1722'
Fri Mar  2 10:05:23 2012 us=862953 Socket Buffers: R=[124928->131072] S=[124928->131072]
Fri Mar  2 10:05:23 2012 us=862966 UDPv4 link local: [undef]
Fri Mar  2 10:05:23 2012 us=862983 UDPv4 link remote: [AF_INET]108.171.113.108:4672
Fri Mar  2 10:05:24 2012 us=64073 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:05:25 2012 us=517681 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:05:28 2012 us=223837 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:05:31 2012 us=126710 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:05:32 2012 us=737723 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:05:35 2012 us=629742 NOTE: --mute triggered...
^CFri Mar  2 10:05:46 2012 us=850523 7 variation(s) on previous 5 message(s) suppressed by --mute
Fri Mar  2 10:05:46 2012 us=850551 SIGTERM received, sending exit notification to peer
Fri Mar  2 10:05:49 2012 us=54953 TCP/UDP: Closing socket
Fri Mar  2 10:05:49 2012 us=55007 SIGTERM[soft,exit-with-notification] received, process exiting
```

I then tried the post's solution to the DNS issue (just in case it was that) but returns (as far as I can tell) the same error  messages
```

birbeth@birbeth-desktop:~$ sudo openvpn --cd StrongVPN/ --config ovpn107.ovpn
Fri Mar  2 10:10:53 2012 us=723895 Current Parameter Settings:
Fri Mar  2 10:10:53 2012 us=723968   config = 'ovpn107.ovpn'
Fri Mar  2 10:10:53 2012 us=723980   mode = 0
Fri Mar  2 10:10:53 2012 us=723991   persist_config = DISABLED
Fri Mar  2 10:10:53 2012 us=724001   persist_mode = 1
Fri Mar  2 10:10:53 2012 us=724011 NOTE: --mute triggered...
Fri Mar  2 10:10:53 2012 us=724031 256 variation(s) on previous 5 message(s) suppressed by --mute
Fri Mar  2 10:10:53 2012 us=724045 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Fri Mar  2 10:10:53 2012 us=724125 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Fri Mar  2 10:10:53 2012 us=724138 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Mar  2 10:10:53 2012 us=724859 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Mar  2 10:10:53 2012 us=812577 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Fri Mar  2 10:10:53 2012 us=812623 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Mar  2 10:10:53 2012 us=812636 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Mar  2 10:10:53 2012 us=812668 LZO compression initialized
Fri Mar  2 10:10:53 2012 us=812740 Control Channel MTU parms [ L:1546 D:166 EF:66 EB:0 ET:0 EL:0 ]
Fri Mar  2 10:10:53 2012 us=812809 Data Channel MTU parms [ L:1546 D:1390 EF:46 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Mar  2 10:10:53 2012 us=812821 Fragmentation MTU parms [ L:1546 D:1390 EF:45 EB:135 ET:1 EL:0 AF:3/1 ]
Fri Mar  2 10:10:53 2012 us=812841 Local Options String: 'V4,dev-type tun,link-mtu 1546,tun-mtu 1500,proto UDPv4,comp-lzo,mtu-dynamic,keydir 1,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-client'
Fri Mar  2 10:10:53 2012 us=812852 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1546,tun-mtu 1500,proto UDPv4,comp-lzo,mtu-dynamic,keydir 0,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-server'
Fri Mar  2 10:10:53 2012 us=812873 Local Options hash (VER=V4): '551868c6'
Fri Mar  2 10:10:53 2012 us=812887 Expected Remote Options hash (VER=V4): 'e34c1722'
Fri Mar  2 10:10:53 2012 us=812906 Socket Buffers: R=[124928->131072] S=[124928->131072]
Fri Mar  2 10:10:53 2012 us=812919 UDPv4 link local: [undef]
Fri Mar  2 10:10:53 2012 us=812936 UDPv4 link remote: [AF_INET]108.171.113.108:4672
Fri Mar  2 10:10:54 2012 us=13375 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:10:55 2012 us=390189 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:10:57 2012 us=943381 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:10:59 2012 us=319954 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:11:01 2012 us=872263 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:11:03 2012 us=248449 NOTE: --mute triggered...
^CFri Mar  2 10:11:10 2012 us=909280 5 variation(s) on previous 5 message(s) suppressed by --mute
Fri Mar  2 10:11:10 2012 us=909308 SIGTERM received, sending exit notification to peer
Fri Mar  2 10:11:12 2012 us=160425 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Fri Mar  2 10:11:12 2012 us=160559 TCP/UDP: Closing socket
Fri Mar  2 10:11:12 2012 us=160591 SIGTERM[soft,exit-with-notification] received, process exiting
```

---

### Post by carranty on 2012-03-02
I know things are fine on the StrongVPN side of things (and my router), since I can connect from my (rooted) Android phone just fine using the same configuration file I'm trying to use here.

---

### Post by carranty on 2012-03-04
bump

---

### Post by nothingspecial on 2012-03-04
Hi, this tutorial is for 10.10.

[http://vpnblog.info/ubuntu-gopenvpn-strongvpn.html](http://vpnblog.info/ubuntu-gopenvpn-strongvpn.html)

Have no idea whether it will work or not.

---

### Post by carranty on 2012-03-04
> **nothingspecial said:**
> Hi, this tutorial is for 10.10.

[http://vpnblog.info/ubuntu-gopenvpn-strongvpn.html](http://vpnblog.info/ubuntu-gopenvpn-strongvpn.html)

Have no idea whether it will work or not.

Nope, same problem as when trying to connect via network manager, it just times out after a while.

---

### Post by carranty on 2012-03-19
I'm still struggling with this.  On my PC I've managed to enable the vpn connection but now can't turn it off.  I probably could do by uninstalling openvpn but then I may never get it working again. I'd rather it be permanently connected than not able to connect at all.  However I still can't get it to work at all on the laptop (both connect wirelessly) even though they both are running 10.04.

---

### Post by agnewton on 2013-01-24
This thread is approaching one year old, I hope that someone will see my tardy post.

I, too, am having the same issues with respect to using StrongVPN with 10.04 LTS.  Did you ever find a solution?

Thanks.

---

### Post by agnewton on 2013-01-25
I'll post my functional solution to the similar problem that was part of this thread on how to get OpenVPN working with StrongVPN.

I have been able to successfully use the installers for the Windows and Mac OS systems to setup my VPN access.   But have been unable to obtain a VPN connection using Linux via the network-manager-openvpn GUIs.

I have followed the instructions on the VPN Blog recommended by the StrongVPN tech support person and in this thread (here: [http://vpnblog.info/ubuntu-openvpn-strongvpn-tutorial.html](http://vpnblog.info/ubuntu-openvpn-strongvpn-tutorial.html)) and considered the discussion in the forum found here: [http://strongvpn.com/forum/viewtopic.php?id=169](http://strongvpn.com/forum/viewtopic.php?id=169).  Neither approach led to a GUI launched VPN connection (i.e. through the network-manager-openvpn-gnome gui).  

I am running Ubuntu 10.04 LTS (64 bit).  I also tried on virtual machines with an Ubuntu 10.04 LTS (32 bit); Ubuntu 12.04.LTS; and OpenSUSE 12.2 (64 bit). 

With the GUI network managers for these OSs, some give false positives, others just time out, or the connection fails (no VPN secrets).  The KDE network manager in OpenSUSE gives a false "connected" message, but the "What's My IP?" test does not indicate the VPN IP and eventually, the connection times out.  

I can access the VPN with the *.ovpn file through the command line in all OSs, but only if I am the superuser (sudo).  I used this link as a reference to understand how to launch an openvpn configuration from the Terminal: [http://askubuntu.com/questions/27168/config-import-on-network-manager-openvpn](http://askubuntu.com/questions/27168/config-import-on-network-manager-openvpn)
As the users in the linked thread suggest, I keep "Available to all users" unchecked and I am a member of the netdev group, but I cannot launch the VPN configuration from the command line through my normal user account or through the network-manager-openvpn-gnome.  Checking "What's my IP?" in a browser in Ubuntu 10.04 LTS and 12.04 LTS (64 bit) indicates that I am, indeed, connected via VPN.   

The 32 bit Ubuntu 10.04 LTS and the 64 bit OpenSUSE do appear to indicate that I am connected (no failed connection messages in the terminal and an ongoing process seems to be running in these terminals).  However, these two virtual machines do not indicate the correct IP in a browser test and, actually, cannot access the internet.  The problem with these two installations could be my bad, I only created them for my diagnostic tests.

For what it's worth, these are my results.  They may be of interest to you if you're trying to sort out OpenVPN issues and are relatively new at this (as I remain).

The question I have and would be glad for any suggestions, "Is there a desktop GUI that I can use to stop and start the VPN without having to use the Terminal as a super user?"  I suppose I could create a launcher icon in the panel to start the VPN, could you add the disconnect function to the same launcher to complete the loop?

Any input is welcome.  Thanks for reading.

---

### Post by d4m1r on 2013-01-25
I don't know about 10.10 but in 12.04 LTS and even going back to 11.04/11.10, I could configure, connect,  and disconnect from an OpenVPN server all from the Network Manager UI.

---

