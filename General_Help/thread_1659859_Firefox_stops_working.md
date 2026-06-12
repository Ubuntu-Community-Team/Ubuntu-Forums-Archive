---
title: "Firefox stops working"
date: 2011-01-04
forum: General Help
---

### Post by jock mackay on 2011-01-04
I am really new to this.
Using 10.4 on a new dell notebook with Firefox 3.6.13, and accessing internet through a BT Hub.

Firefox works away for a couple of minutes, but after opening a few tabs I find that I can not connect to sites. Error messages include Server not Found, and Connection has timed out. As far as I can tell the wireless connection is operating (certainly I can see the radiating signal at the top of the page, and the wireless is working on other computers while I have this problem.)

Rebooting gets firefox working again, but soon the problem re-emerges.

I suspect this is not a new issue, but have not found a definitive answer to the problem.

---

### Post by dandnsmith on 2011-01-04
I think you can rule out the firefox/ubuntu as being, in itself, a problem, and concentrate on things like memory problems (many tabs open?), local interference, BTHub problem.

Only other thing might be some update you have applied before the problem started.

When it happens, you could consider getting a terminal window up,
looking at the state of things via ipconfig, iwconfig, and ping sites by name and also by IP address.

---

### Post by lithopsian on 2011-01-04
Are you running a bit torrent server?

---

### Post by ajgreeny on 2011-01-04
Have you disabled ipv6 in the **about:config** page of FF.  If not type **about:config** in the addressbar, ignore the warning, search for ipv6 in the filter, and make sure it ends true:-

     network.dns.disableIPv6                                   user set                                  boolean                                         true 

 if it says false at the end, double click it to toggle to true, and you may find FF is much faster.

If that does not help it may be that your profile is corrupt in some  way, so rename your home folder ~/.mozilla and restart FF.  Maybe it  will now run as it should.  You can then get your bookmarks back from  the old profile folder.

---

### Post by jock mackay on 2011-01-05
I have adjusted ipv6 as you suggested and rebooted, and so far so good. I will try for a day and see how it goes.
I did say I am a novice at Ubuntu, so I confess I do not know how to modify the home folder, and I do not understand the significance of Bit Torrent, but I see I have software loaded called Transmission which refers to Bit Torrent.

Something new to learn every day.

---

### Post by jock mackay on 2011-01-05
> **jock mackay said:**
> I have adjusted ipv6 as you suggested and rebooted, and so far so good. I will try for a day and see how it goes.
I did say I am a novice at Ubuntu, so I confess I do not know how to modify the home folder, and I do not understand the significance of Bit Torrent, but I see I have software loaded called Transmission which refers to Bit Torrent.

Something new to learn every day.
I guess I spoke too soon. The server time-out issues are as bad as they originally were. One thing I noticed is a reference to  ipv4 when i checked that the ipv6 setting was still "true" - has this any relevance?

---

### Post by Chris Seelig on 2011-01-05
Next time it happens fire up a terminal (Applications/Accessories/Terminal or similar  ) and run the following commands.

[B]ifconfig -a
netstat -rn[/B]

If you know the IP address of your router (likely 192.168.1.1 or something similar)

**ping -nc5 192.168.1.1**

obviously replace the number with your routers number
if that works then (the ip is not important as long as its something not on your network)

**traceroute -nm 5 7.7.7.7**

Post the results

Chris

---

### Post by jock mackay on 2011-01-05
> **Chris Seelig said:**
> Next time it happens fire up a terminal (Applications/Accessories/Terminal or similar  ) and run the following commands.

[B]ifconfig -a
netstat -rn[/B]

If you know the IP address of your router (likely 192.168.1.1 or something similar)

**ping -nc5 192.168.1.1**

obviously replace the number with your routers number
if that works then (the ip is not important as long as its something not on your network)

**traceroute -nm 5 7.7.7.7**

Post the results

Chris
Here is what I got last time Firefox stopped reaching Servers.

Version:1.0 StartHTML:0000000167 EndHTML:0000005491 StartFragment:0000000454 EndFragment:0000005475    	 	 	 	p { margin-bottom: 0.21cm; }  tom@eleanor-laptop:~$ ifconfig -a
 eth0      Link encap:Ethernet  HWaddr 5c:26:0a:0d:1c:07   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:26 Base address:0x4000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:30 errors:0 dropped:0 overruns:0 frame:0
           TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:2064 (2.0 KB)  TX bytes:2064 (2.0 KB)
 

 wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:fe:22:18   
           inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
           inet6 addr: fe80::72f1:a1ff:fefe:2218/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:4592 errors:0 dropped:0 overruns:0 frame:0
           TX packets:4582 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:3751461 (3.7 MB)  TX bytes:798994 (798.9 KB)
           Interrupt:17 Memory:f80d0000-f80d0100  
 

 tom@eleanor-laptop:~$  
 

 

 tom@eleanor-laptop:~$ netstart -rn  
 No command 'netstart' found, did you mean:  
  Command 'netstat' from package 'net-tools' (main)  
 netstart: command not found  
 tom@eleanor-laptop:~$ netstat -rn  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface  
 192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0  
 169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0  
 
[LIST=1]
[LIST=1]
[LIST=1]
[LIST=1]
[*]192.168.1.254   0.0.0.0         				UG        0 0          0 wlan0  				
[/LIST]
[/LIST]
[/LIST]
[/LIST]
 

 

 tom@eleanor-laptop:~$ ping -nc5 192.168.1.254  
 PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.  
 64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=10.7 ms  
 64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1.36 ms  
 64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=7.59 ms  
 64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=1.34 ms  
 64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=1.87 ms  
 

 --- 192.168.1.254 ping statistics ---  
 5 packets transmitted, 5 received, 0% packet loss, time 4006ms  
 rtt min/avg/max/mdev = 1.340/4.591/10.792/3.894 ms  
 

 

 tom@eleanor-laptop:~$ traceroute nm 5.7.7.7.7  
 The program 'traceroute' can be found in the following packages:  
  * traceroute  
  * traceroute-nanog  
 Try: sudo apt-get install <selected package>  
 tom@eleanor-laptop:~$ 



I hope that makes sense!.

---

### Post by jock mackay on 2011-01-05
I omitted to post this last time.

Version:1.0 StartHTML:0000000167 EndHTML:0000001153 StartFragment:0000000454 EndFragment:0000001137    	 	 	 	p { margin-bottom: 0.21cm; }  eleanor@eleanor-laptop:~$ traceroute -nm 5 7.7.7.7  
 traceroute to 7.7.7.7 (7.7.7.7), 5 hops max, 60 byte packets  
  1  192.168.1.254  89.658 ms  89.450 ms  89.322 ms  
  2  217.47.187.186  39.340 ms  39.942 ms  39.848 ms  
  3  217.47.187.161  39.754 ms  41.778 ms  43.345 ms  
  4  213.1.69.74  54.208 ms  54.860 ms  56.639 ms  
  5  213.120.157.10  59.210 ms  60.594 ms  63.163 ms  
 eleanor@eleanor-laptop:~$

---

### Post by Chris Seelig on 2011-01-05
Something odd about the netstat output, did it cut and paste badly? But the traceroute would seem to confirm that basic connectivity and routing is in place.

Does the problem start a few minutes after starting firefox, or a few minutes after rebooting? If you wait long enough before starting firefox does the problem occur immediately.

Few more tests.

when its not working try pinging the website thats failing (some sites will block ping so use one you know normaly works, [www.bbc.co.uk](www.bbc.co.uk) is good)

**ping -c5 [www.bbc.co.uk](www.bbc.co.uk)**

Your using the name now so that should show if you have a DNS resolution problem.
Hopefully you have wget installed, so if the ping works try

**wget [http://www.bbc.co.uk](http://www.bbc.co.uk)**

If you get an index.html file then you have pretty much confirmed that its not a network problem.

If you get errors from either command then they will probably tell you whats wrong.

Chris

---

### Post by jock mackay on 2011-01-06
I ran the netstat programme again, and got more than I bargained for, but here it is in all its glory.
Version:1.0 StartHTML:0000000167 EndHTML:0000056513 StartFragment:0000000454 EndFragment:0000056497    	 	 	 	p { margin-bottom: 0.21cm; }  unix  3      [ ]         STREAM     CONNECTED     13897     
 unix  3      [ ]         STREAM     CONNECTED     12982    @/tmp/.X11-unix/X1  
 unix  3      [ ]         STREAM     CONNECTED     12981     
 unix  3      [ ]         STREAM     CONNECTED     12968    @/tmp/.X11-unix/X1  
 unix  3      [ ]         STREAM     CONNECTED     12967     
 unix  3      [ ]         STREAM     CONNECTED     12866    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     12865     
 unix  3      [ ]         STREAM     CONNECTED     12815    @/tmp/.X11-unix/X1  
 unix  3      [ ]         STREAM     CONNECTED     12814     
 unix  3      [ ]         STREAM     CONNECTED     12805    /var/run/acpid.socket  
 unix  3      [ ]         STREAM     CONNECTED     12804     
 unix  3      [ ]         STREAM     CONNECTED     12738    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     12737     
 unix  3      [ ]         STREAM     CONNECTED     12355    @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     12354     
 unix  3      [ ]         STREAM     CONNECTED     12334    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     12333     
 unix  3      [ ]         STREAM     CONNECTED     12328     
 unix  3      [ ]         STREAM     CONNECTED     12327     
 unix  3      [ ]         STREAM     CONNECTED     12323    /tmp/orbit-eleanor/linc-1186-0-64884462520e6  
 unix  3      [ ]         STREAM     CONNECTED     12322     
 unix  3      [ ]         STREAM     CONNECTED     12319    /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     12318     
 unix  3      [ ]         STREAM     CONNECTED     12315    @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     12314     
 unix  3      [ ]         STREAM     CONNECTED     12313    @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     12312     
 unix  3      [ ]         STREAM     CONNECTED     12308    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     12307     
 unix  3      [ ]         STREAM     CONNECTED     8004     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     8003      
 unix  3      [ ]         STREAM     CONNECTED     7991     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7990      
 unix  3      [ ]         STREAM     CONNECTED     7944     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7943      
 unix  3      [ ]         STREAM     CONNECTED     7941     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7940      
 unix  3      [ ]         STREAM     CONNECTED     7939     /tmp/orbit-eleanor/linc-57e-0-179f388ca374e  
 unix  3      [ ]         STREAM     CONNECTED     7938      
 unix  3      [ ]         STREAM     CONNECTED     7935     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7934      
 unix  3      [ ]         STREAM     CONNECTED     7930     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7929      
 unix  3      [ ]         STREAM     CONNECTED     7927     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7926      
 unix  3      [ ]         STREAM     CONNECTED     7739     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7738      
 unix  3      [ ]         STREAM     CONNECTED     7734     /tmp/orbit-eleanor/linc-543-0-7c9e9a43b68f4  
 unix  3      [ ]         STREAM     CONNECTED     7733      
 unix  3      [ ]         STREAM     CONNECTED     7730     /tmp/orbit-eleanor/linc-54d-0-68597cbde2349  
 unix  3      [ ]         STREAM     CONNECTED     7729      
 unix  3      [ ]         STREAM     CONNECTED     7726     /tmp/orbit-eleanor/linc-550-0-1254175b29290  
 unix  3      [ ]         STREAM     CONNECTED     7725      
 unix  3      [ ]         STREAM     CONNECTED     7724     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     7723      
 unix  3      [ ]         STREAM     CONNECTED     7722     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7721      
 unix  3      [ ]         STREAM     CONNECTED     7718     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7717      
 unix  3      [ ]         STREAM     CONNECTED     7716     /tmp/orbit-eleanor/linc-550-0-1254175b29290  
 unix  3      [ ]         STREAM     CONNECTED     7715      
 unix  3      [ ]         STREAM     CONNECTED     7712     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7711      
 unix  3      [ ]         STREAM     CONNECTED     7709     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7708      
 unix  3      [ ]         STREAM     CONNECTED     7707     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     7706      
 unix  3      [ ]         STREAM     CONNECTED     7702     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7701      
 unix  3      [ ]         STREAM     CONNECTED     7697     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7696      
 unix  3      [ ]         STREAM     CONNECTED     7651     /tmp/orbit-eleanor/linc-54d-0-68597cbde2349  
 unix  3      [ ]         STREAM     CONNECTED     7650      
 unix  3      [ ]         STREAM     CONNECTED     7649     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7648      
 unix  3      [ ]         STREAM     CONNECTED     7646     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7645      
 unix  3      [ ]         STREAM     CONNECTED     7640     /tmp/orbit-eleanor/linc-54d-0-68597cbde2349  
 unix  3      [ ]         STREAM     CONNECTED     7639      
 unix  3      [ ]         STREAM     CONNECTED     7636     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     7635      
 unix  3      [ ]         STREAM     CONNECTED     7583     /tmp/orbit-eleanor/linc-543-0-7c9e9a43b68f4  
 unix  3      [ ]         STREAM     CONNECTED     7582      
 unix  3      [ ]         STREAM     CONNECTED     7581     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     7580      
 unix  3      [ ]         STREAM     CONNECTED     7577     /tmp/orbit-eleanor/linc-543-0-7c9e9a43b68f4  
 unix  3      [ ]         STREAM     CONNECTED     7576      
 unix  3      [ ]         STREAM     CONNECTED     7573     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7572      
 unix  3      [ ]         STREAM     CONNECTED     7570     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7569      
 unix  3      [ ]         STREAM     CONNECTED     7568     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     7567      
 unix  3      [ ]         STREAM     CONNECTED     7563     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7562      
 unix  3      [ ]         STREAM     CONNECTED     7239     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7238      
 unix  3      [ ]         STREAM     CONNECTED     7230     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7229      
 unix  3      [ ]         STREAM     CONNECTED     7227     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7226      
 unix  3      [ ]         STREAM     CONNECTED     7178     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     7177      
 unix  3      [ ]         STREAM     CONNECTED     7149     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7148      
 unix  3      [ ]         STREAM     CONNECTED     7070     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7069      
 unix  3      [ ]         STREAM     CONNECTED     7063     /tmp/orbit-eleanor/linc-504-0-252775a9ba5a9  
 unix  3      [ ]         STREAM     CONNECTED     7062      
 unix  3      [ ]         STREAM     CONNECTED     7059     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7058      
 unix  3      [ ]         STREAM     CONNECTED     7053     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7052      
 unix  3      [ ]         STREAM     CONNECTED     7050     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7049      
 unix  3      [ ]         STREAM     CONNECTED     6965     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6964      
 unix  3      [ ]         STREAM     CONNECTED     6951     /home/eleanor/.pulse/35841d8b96cc824cdf3c9f9e4d0e40de-runtime/native  
 unix  3      [ ]         STREAM     CONNECTED     6950      
 unix  3      [ ]         STREAM     CONNECTED     6941     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6940      
 unix  3      [ ]         STREAM     CONNECTED     6928     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6927      
 unix  3      [ ]         STREAM     CONNECTED     6914     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6913      
 unix  3      [ ]         STREAM     CONNECTED     6911     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6910      
 unix  3      [ ]         STREAM     CONNECTED     6896     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6895      
 unix  3      [ ]         STREAM     CONNECTED     6894     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6893      
 unix  3      [ ]         STREAM     CONNECTED     6890     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6889      
 unix  3      [ ]         STREAM     CONNECTED     6865     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6864      
 unix  3      [ ]         STREAM     CONNECTED     6861     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6860      
 unix  2      [ ]         DGRAM                    6855      
 unix  3      [ ]         STREAM     CONNECTED     6854     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6853      
 unix  3      [ ]         STREAM     CONNECTED     6849     /tmp/orbit-eleanor/linc-4e7-0-575a06f915e71  
 unix  3      [ ]         STREAM     CONNECTED     6848      
 unix  3      [ ]         STREAM     CONNECTED     6845     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6844      
 unix  3      [ ]         STREAM     CONNECTED     6816     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6815      
 unix  3      [ ]         STREAM     CONNECTED     6809     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6808      
 unix  3      [ ]         STREAM     CONNECTED     6778     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6777      
 unix  3      [ ]         STREAM     CONNECTED     6765     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6764      
 unix  3      [ ]         STREAM     CONNECTED     6762     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6761      
 unix  3      [ ]         STREAM     CONNECTED     6755     /tmp/orbit-eleanor/linc-4cf-0-2c4a27a8d593  
 unix  3      [ ]         STREAM     CONNECTED     6754      
 unix  3      [ ]         STREAM     CONNECTED     6751     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6750      
 unix  3      [ ]         STREAM     CONNECTED     6747     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6746      
 unix  3      [ ]         STREAM     CONNECTED     6707     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6706      
 unix  3      [ ]         STREAM     CONNECTED     6702     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6701      
 unix  3      [ ]         STREAM     CONNECTED     6690     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6689      
 unix  3      [ ]         STREAM     CONNECTED     6688     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6687      
 unix  3      [ ]         STREAM     CONNECTED     6686     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6685      
 unix  3      [ ]         STREAM     CONNECTED     6682     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6681      
 unix  3      [ ]         STREAM     CONNECTED     6680     /tmp/orbit-eleanor/linc-4bd-0-9db6d861d9cb  
 unix  3      [ ]         STREAM     CONNECTED     6679      
 unix  3      [ ]         STREAM     CONNECTED     6678     /tmp/orbit-eleanor/linc-4bd-0-9db6d861d9cb  
 unix  3      [ ]         STREAM     CONNECTED     6677      
 unix  3      [ ]         STREAM     CONNECTED     6676     /tmp/orbit-eleanor/linc-4bf-0-73454d1a19466  
 unix  3      [ ]         STREAM     CONNECTED     6675      
 unix  3      [ ]         STREAM     CONNECTED     6674     /tmp/orbit-eleanor/linc-4bf-0-73454d1a19466  
 unix  3      [ ]         STREAM     CONNECTED     6673      
 unix  3      [ ]         STREAM     CONNECTED     6672     /tmp/orbit-eleanor/linc-4c2-0-13b5d4cf1e004  
 unix  3      [ ]         STREAM     CONNECTED     6671      
 unix  3      [ ]         STREAM     CONNECTED     6670     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6669      
 unix  3      [ ]         STREAM     CONNECTED     6667     /tmp/orbit-eleanor/linc-4c2-0-13b5d4cf1e004  
 unix  3      [ ]         STREAM     CONNECTED     6666      
 unix  3      [ ]         STREAM     CONNECTED     6668     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6664      
 unix  3      [ ]         STREAM     CONNECTED     6665     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6663      
 unix  3      [ ]         STREAM     CONNECTED     6662     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6661      
 unix  3      [ ]         STREAM     CONNECTED     6660     /tmp/orbit-eleanor/linc-4be-0-27a018014b6f  
 unix  3      [ ]         STREAM     CONNECTED     6659      
 unix  3      [ ]         STREAM     CONNECTED     6658     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6657      
 unix  3      [ ]         STREAM     CONNECTED     6656     /tmp/orbit-eleanor/linc-4b7-0-16b47db210b43  
 unix  3      [ ]         STREAM     CONNECTED     6655      
 unix  3      [ ]         STREAM     CONNECTED     6652     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6651      
 unix  3      [ ]         STREAM     CONNECTED     6650     /tmp/orbit-eleanor/linc-4be-0-27a018014b6f  
 unix  3      [ ]         STREAM     CONNECTED     6649      
 unix  3      [ ]         STREAM     CONNECTED     6648     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6647      
 unix  3      [ ]         STREAM     CONNECTED     6645     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6644      
 unix  3      [ ]         STREAM     CONNECTED     6641     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6640      
 unix  3      [ ]         STREAM     CONNECTED     6639     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6638      
 unix  3      [ ]         STREAM     CONNECTED     6637     /tmp/orbit-eleanor/linc-4b7-0-16b47db210b43  
 unix  3      [ ]         STREAM     CONNECTED     6636      
 unix  3      [ ]         STREAM     CONNECTED     6635     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6634      
 unix  3      [ ]         STREAM     CONNECTED     6631     /tmp/orbit-eleanor/linc-4c2-0-13b5d4cf1e004  
 unix  3      [ ]         STREAM     CONNECTED     6629      
 unix  3      [ ]         STREAM     CONNECTED     6626     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6625      
 unix  3      [ ]         STREAM     CONNECTED     6642     /tmp/orbit-eleanor/linc-4bd-0-9db6d861d9cb  
 unix  3      [ ]         STREAM     CONNECTED     6624      
 unix  3      [ ]         STREAM     CONNECTED     6621     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6620     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6619      
 unix  3      [ ]         STREAM     CONNECTED     6618      
 unix  3      [ ]         STREAM     CONNECTED     6633     /tmp/orbit-eleanor/linc-4bf-0-73454d1a19466  
 unix  3      [ ]         STREAM     CONNECTED     6617      
 unix  3      [ ]         STREAM     CONNECTED     6614     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6613      
 unix  3      [ ]         STREAM     CONNECTED     6609     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6608      
 unix  3      [ ]         STREAM     CONNECTED     6610     /tmp/orbit-eleanor/linc-4be-0-27a018014b6f  
 unix  3      [ ]         STREAM     CONNECTED     6604      
 unix  3      [ ]         STREAM     CONNECTED     6601     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6600      
 unix  3      [ ]         STREAM     CONNECTED     6630     /tmp/orbit-eleanor/linc-4c3-0-14002182d179  
 unix  3      [ ]         STREAM     CONNECTED     6599      
 unix  3      [ ]         STREAM     CONNECTED     6598     /tmp/orbit-eleanor/linc-4c3-0-14002182d179  
 unix  3      [ ]         STREAM     CONNECTED     6597      
 unix  3      [ ]         STREAM     CONNECTED     6596     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6595      
 unix  3      [ ]         STREAM     CONNECTED     6593     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6592      
 unix  3      [ ]         STREAM     CONNECTED     6605     /tmp/orbit-eleanor/linc-4b7-0-16b47db210b43  
 unix  3      [ ]         STREAM     CONNECTED     6589      
 unix  3      [ ]         STREAM     CONNECTED     6586     /tmp/orbit-eleanor/linc-4c3-0-14002182d179  
 unix  3      [ ]         STREAM     CONNECTED     6585      
 unix  3      [ ]         STREAM     CONNECTED     6584     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6583      
 unix  3      [ ]         STREAM     CONNECTED     6580     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6579      
 unix  3      [ ]         STREAM     CONNECTED     6549     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6545      
 unix  3      [ ]         STREAM     CONNECTED     6548     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6544      
 unix  3      [ ]         STREAM     CONNECTED     6546     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6543      
 unix  3      [ ]         STREAM     CONNECTED     6541     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6539      
 unix  3      [ ]         STREAM     CONNECTED     6540     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6534      
 unix  3      [ ]         STREAM     CONNECTED     6291     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6290      
 unix  3      [ ]         STREAM     CONNECTED     6254     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6253      
 unix  3      [ ]         STREAM     CONNECTED     6251     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6250      
 unix  3      [ ]         STREAM     CONNECTED     6249     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6248      
 unix  3      [ ]         STREAM     CONNECTED     6246     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6245      
 unix  3      [ ]         STREAM     CONNECTED     6240     /tmp/orbit-eleanor/linc-4b1-0-30255ae846e9d  
 unix  3      [ ]         STREAM     CONNECTED     6239      
 unix  3      [ ]         STREAM     CONNECTED     6236     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6235      
 unix  3      [ ]         STREAM     CONNECTED     6229     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6228      
 unix  3      [ ]         STREAM     CONNECTED     6225     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6224      
 unix  3      [ ]         STREAM     CONNECTED     6177     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     6176      
 unix  3      [ ]         STREAM     CONNECTED     6173     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6172      
 unix  3      [ ]         STREAM     CONNECTED     6167     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6166      
 unix  3      [ ]         STREAM     CONNECTED     6161     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6160      
 unix  3      [ ]         STREAM     CONNECTED     6147     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6146      
 unix  3      [ ]         STREAM     CONNECTED     6145     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6144      
 unix  3      [ ]         STREAM     CONNECTED     6129     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6128      
 unix  3      [ ]         STREAM     CONNECTED     6122     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6121      
 unix  3      [ ]         STREAM     CONNECTED     6094     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6093      
 unix  3      [ ]         STREAM     CONNECTED     6090     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6089      
 unix  3      [ ]         STREAM     CONNECTED     6086     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6085      
 unix  3      [ ]         STREAM     CONNECTED     6080     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6079      
 unix  3      [ ]         STREAM     CONNECTED     6069     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6068      
 unix  3      [ ]         STREAM     CONNECTED     6062     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6061      
 unix  3      [ ]         STREAM     CONNECTED     6060     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6059      
 unix  3      [ ]         STREAM     CONNECTED     6054     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6053      
 unix  3      [ ]         STREAM     CONNECTED     6048     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6047      
 unix  3      [ ]         STREAM     CONNECTED     6035     /tmp/orbit-eleanor/linc-46f-0-6d21f7889d303  
 unix  3      [ ]         STREAM     CONNECTED     6034      
 unix  3      [ ]         STREAM     CONNECTED     6030     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6029      
 unix  3      [ ]         STREAM     CONNECTED     6024     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6023      
 unix  3      [ ]         STREAM     CONNECTED     6022     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6021      
 unix  3      [ ]         STREAM     CONNECTED     6020     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6019      
 unix  3      [ ]         STREAM     CONNECTED     6015     /tmp/orbit-eleanor/linc-471-0-67ac7c9c8dd42  
 unix  3      [ ]         STREAM     CONNECTED     6014      
 unix  3      [ ]         STREAM     CONNECTED     6011     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6010      
 unix  3      [ ]         STREAM     CONNECTED     6009     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6008      
 unix  3      [ ]         STREAM     CONNECTED     6001     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6000      
 unix  3      [ ]         STREAM     CONNECTED     5998     /tmp/orbit-eleanor/linc-46d-0-aefa4007e7c2  
 unix  3      [ ]         STREAM     CONNECTED     5994      
 unix  3      [ ]         STREAM     CONNECTED     5991     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5990      
 unix  3      [ ]         STREAM     CONNECTED     5986     /tmp/orbit-eleanor/linc-472-0-1188f1da7ad70  
 unix  3      [ ]         STREAM     CONNECTED     5985      
 unix  3      [ ]         STREAM     CONNECTED     5982     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5981      
 unix  3      [ ]         STREAM     CONNECTED     5978     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5977      
 unix  3      [ ]         STREAM     CONNECTED     5973     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5972      
 unix  3      [ ]         STREAM     CONNECTED     5971     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5970      
 unix  3      [ ]         STREAM     CONNECTED     5968     /tmp/orbit-eleanor/linc-46b-0-32b6295e6336b  
 unix  3      [ ]         STREAM     CONNECTED     5967      
 unix  3      [ ]         STREAM     CONNECTED     5961     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5960      
 unix  3      [ ]         STREAM     CONNECTED     5963     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5959      
 unix  3      [ ]         STREAM     CONNECTED     5964     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5958      
 unix  3      [ ]         STREAM     CONNECTED     5956     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5955      
 unix  3      [ ]         STREAM     CONNECTED     5954     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     5953      
 unix  3      [ ]         STREAM     CONNECTED     5950     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5949      
 unix  3      [ ]         STREAM     CONNECTED     5948     /home/eleanor/.pulse/35841d8b96cc824cdf3c9f9e4d0e40de-runtime/native  
 unix  3      [ ]         STREAM     CONNECTED     5947      
 unix  3      [ ]         STREAM     CONNECTED     5944     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5943      
 unix  3      [ ]         STREAM     CONNECTED     5941     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5940      
 unix  3      [ ]         STREAM     CONNECTED     5939     /tmp/orbit-eleanor/linc-476-0-5b97fc503c24e  
 unix  3      [ ]         STREAM     CONNECTED     5937      
 unix  3      [ ]         STREAM     CONNECTED     5934     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5933      
 unix  3      [ ]         STREAM     CONNECTED     5926     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5925      
 unix  3      [ ]         STREAM     CONNECTED     5922     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5920      
 unix  2      [ ]         DGRAM                    5872      
 unix  3      [ ]         STREAM     CONNECTED     5871     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5870      
 unix  3      [ ]         STREAM     CONNECTED     5866     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5865      
 unix  3      [ ]         STREAM     CONNECTED     5864     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5863      
 unix  3      [ ]         STREAM     CONNECTED     5861     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5860      
 unix  3      [ ]         STREAM     CONNECTED     5857     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5856      
 unix  3      [ ]         STREAM     CONNECTED     5854     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5853      
 unix  3      [ ]         STREAM     CONNECTED     5850     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5849      
 unix  3      [ ]         STREAM     CONNECTED     5848     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5847      
 unix  3      [ ]         STREAM     CONNECTED     5834     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5833      
 unix  3      [ ]         STREAM     CONNECTED     5832     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5831      
 unix  3      [ ]         STREAM     CONNECTED     5550     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5549      
 unix  3      [ ]         STREAM     CONNECTED     5548     /tmp/orbit-eleanor/linc-46a-0-7c66b76f9cc94  
 unix  3      [ ]         STREAM     CONNECTED     5547      
 unix  3      [ ]         STREAM     CONNECTED     5544     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5543      
 unix  3      [ ]         STREAM     CONNECTED     5540     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5539      
 unix  3      [ ]         STREAM     CONNECTED     5536     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5535      
 unix  3      [ ]         STREAM     CONNECTED     5528     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5527      
 unix  3      [ ]         STREAM     CONNECTED     5526     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5525      
 unix  3      [ ]         STREAM     CONNECTED     5514     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5513      
 unix  3      [ ]         STREAM     CONNECTED     5479     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5478      
 unix  3      [ ]         STREAM     CONNECTED     5476     /tmp/orbit-eleanor/linc-45f-0-53d6c5eb5e3b9  
 unix  3      [ ]         STREAM     CONNECTED     5475      
 unix  3      [ ]         STREAM     CONNECTED     5472     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5471      
 unix  3      [ ]         STREAM     CONNECTED     5467     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5466      
 unix  3      [ ]         STREAM     CONNECTED     5463     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5462      
 unix  3      [ ]         STREAM     CONNECTED     5458     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5457      
 unix  3      [ ]         STREAM     CONNECTED     5436     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5435      
 unix  2      [ ]         DGRAM                    5434      
 unix  3      [ ]         STREAM     CONNECTED     5423     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5422      
 unix  3      [ ]         STREAM     CONNECTED     5353     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5352      
 unix  3      [ ]         STREAM     CONNECTED     5348     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5347      
 unix  3      [ ]         STREAM     CONNECTED     5309     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5308      
 unix  3      [ ]         STREAM     CONNECTED     5303     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5302      
 unix  3      [ ]         STREAM     CONNECTED     5299     /tmp/orbit-eleanor/linc-454-0-4baead3caaf3b  
 unix  3      [ ]         STREAM     CONNECTED     5298      
 unix  3      [ ]         STREAM     CONNECTED     5295     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5294      
 unix  3      [ ]         STREAM     CONNECTED     5288     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5287      
 unix  3      [ ]         STREAM     CONNECTED     5285     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5284      
 unix  3      [ ]         STREAM     CONNECTED     5257     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5256      
 unix  3      [ ]         STREAM     CONNECTED     5142     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5141      
 unix  3      [ ]         STREAM     CONNECTED     5139     /tmp/orbit-eleanor/linc-422-0-2c207fbd568ef  
 unix  3      [ ]         STREAM     CONNECTED     5138      
 unix  3      [ ]         STREAM     CONNECTED     5135     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5134      
 unix  3      [ ]         STREAM     CONNECTED     5131     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5130      
 unix  3      [ ]         STREAM     CONNECTED     4900     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     4899      
 unix  3      [ ]         STREAM     CONNECTED     4859     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     4858      
 unix  3      [ ]         STREAM     CONNECTED     4856     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4855      
 unix  3      [ ]         STREAM     CONNECTED     4852     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4851      
 unix  3      [ ]         STREAM     CONNECTED     4850      
 unix  3      [ ]         STREAM     CONNECTED     4849      
 unix  3      [ ]         STREAM     CONNECTED     4838     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4837      
 unix  3      [ ]         STREAM     CONNECTED     4698     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     4697      
 unix  2      [ ]         DGRAM                    4690      
 unix  3      [ ]         STREAM     CONNECTED     4689     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4688      
 unix  3      [ ]         STREAM     CONNECTED     4684     @/tmp/gdm-session-HoVxjucK  
 unix  3      [ ]         STREAM     CONNECTED     4683      
 unix  3      [ ]         STREAM     CONNECTED     4680     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     4679      
 unix  3      [ ]         STREAM     CONNECTED     4613     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4612      
 unix  2      [ ]         DGRAM                    3921      
 unix  2      [ ]         DGRAM                    3909      
 unix  3      [ ]         STREAM     CONNECTED     3851     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3850      
 unix  2      [ ]         DGRAM                    3849      
 unix  3      [ ]         STREAM     CONNECTED     3820     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3819      
 unix  2      [ ]         DGRAM                    3793      
 unix  3      [ ]         STREAM     CONNECTED     3750     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3749      
 unix  3      [ ]         STREAM     CONNECTED     3712     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3711      
 unix  3      [ ]         STREAM     CONNECTED     3640     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3639      
 unix  2      [ ]         DGRAM                    3561      
 unix  2      [ ]         DGRAM                    3560      
 unix  3      [ ]         STREAM     CONNECTED     3554     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3553      
 unix  3      [ ]         STREAM     CONNECTED     3550     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3549      
 unix  3      [ ]         STREAM     CONNECTED     3531     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3530      
 unix  3      [ ]         STREAM     CONNECTED     3523      
 unix  3      [ ]         STREAM     CONNECTED     3522      
 unix  3      [ ]         STREAM     CONNECTED     3496     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3495      
 unix  3      [ ]         STREAM     CONNECTED     3473     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3472      
 unix  3      [ ]         STREAM     CONNECTED     3471      
 unix  3      [ ]         STREAM     CONNECTED     3470      
 unix  3      [ ]         DGRAM                    2719      
 unix  3      [ ]         DGRAM                    2718      
 unix  3      [ ]         STREAM     CONNECTED     2665     @/com/ubuntu/upstart  
 unix  3      [ ]         STREAM     CONNECTED     2664      
 tom@eleanor-laptop:~$ 



I followed that up with the pinging, and here are the results:-
Version:1.0 StartHTML:0000000167 EndHTML:0000001079 StartFragment:0000000454 EndFragment:0000001063    	 	 	 	p { margin-bottom: 0.21cm; }  tom@eleanor-laptop:~$ ping c5 [www.bbc.co.uk](www.bbc.co.uk)  
 ping: unknown host c5  
 tom@eleanor-laptop:~$  
 tom@eleanor-laptop:~$ wget [http://www.bbc.co.uk](http://www.bbc.co.uk)  
 --2011-01-06 12:46:55--  [http://www.bbc.co.uk/](http://www.bbc.co.uk/)  
 Resolving [www.bbc.co.uk](www.bbc.co.uk)... failed: Name or service not known.  
 wget: unable to resolve host address `[www.bbc.co.uk](www.bbc.co.uk)'  
 tom@eleanor-laptop:~$ 



The problem seems random in relation to when it happens. It is hard to recall a time when I could not access the first site I asked for. Usually it happens when I have abour 3 tabs up and running. Today, I thought it was not going to happen at all, just to spite me, but it did happen after hammering the sites on about 5 tabs for a couple of minutes ... that was when I did the pinging and BBc was one of the sites that was tabbed at the time.


Good luck with this.

---

### Post by jock mackay on 2011-01-08
> **jock mackay said:**
> I ran the netstat programme again, and got more than I bargained for, but here it is in all its glory.
Version:1.0 StartHTML:0000000167 EndHTML:0000056513 StartFragment:0000000454 EndFragment:0000056497    	 	 	 	p { margin-bottom: 0.21cm; }  unix  3      [ ]         STREAM     CONNECTED     13897     
 unix  3      [ ]         STREAM     CONNECTED     12982    @/tmp/.X11-unix/X1  
 unix  3      [ ]         STREAM     CONNECTED     12981     
 unix  3      [ ]         STREAM     CONNECTED     12968    @/tmp/.X11-unix/X1  
 unix  3      [ ]         STREAM     CONNECTED     12967     
 unix  3      [ ]         STREAM     CONNECTED     12866    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     12865     
 unix  3      [ ]         STREAM     CONNECTED     12815    @/tmp/.X11-unix/X1  
 unix  3      [ ]         STREAM     CONNECTED     12814     
 unix  3      [ ]         STREAM     CONNECTED     12805    /var/run/acpid.socket  
 unix  3      [ ]         STREAM     CONNECTED     12804     
 unix  3      [ ]         STREAM     CONNECTED     12738    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     12737     
 unix  3      [ ]         STREAM     CONNECTED     12355    @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     12354     
 unix  3      [ ]         STREAM     CONNECTED     12334    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     12333     
 unix  3      [ ]         STREAM     CONNECTED     12328     
 unix  3      [ ]         STREAM     CONNECTED     12327     
 unix  3      [ ]         STREAM     CONNECTED     12323    /tmp/orbit-eleanor/linc-1186-0-64884462520e6  
 unix  3      [ ]         STREAM     CONNECTED     12322     
 unix  3      [ ]         STREAM     CONNECTED     12319    /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     12318     
 unix  3      [ ]         STREAM     CONNECTED     12315    @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     12314     
 unix  3      [ ]         STREAM     CONNECTED     12313    @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     12312     
 unix  3      [ ]         STREAM     CONNECTED     12308    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     12307     
 unix  3      [ ]         STREAM     CONNECTED     8004     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     8003      
 unix  3      [ ]         STREAM     CONNECTED     7991     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7990      
 unix  3      [ ]         STREAM     CONNECTED     7944     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7943      
 unix  3      [ ]         STREAM     CONNECTED     7941     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7940      
 unix  3      [ ]         STREAM     CONNECTED     7939     /tmp/orbit-eleanor/linc-57e-0-179f388ca374e  
 unix  3      [ ]         STREAM     CONNECTED     7938      
 unix  3      [ ]         STREAM     CONNECTED     7935     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7934      
 unix  3      [ ]         STREAM     CONNECTED     7930     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7929      
 unix  3      [ ]         STREAM     CONNECTED     7927     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7926      
 unix  3      [ ]         STREAM     CONNECTED     7739     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7738      
 unix  3      [ ]         STREAM     CONNECTED     7734     /tmp/orbit-eleanor/linc-543-0-7c9e9a43b68f4  
 unix  3      [ ]         STREAM     CONNECTED     7733      
 unix  3      [ ]         STREAM     CONNECTED     7730     /tmp/orbit-eleanor/linc-54d-0-68597cbde2349  
 unix  3      [ ]         STREAM     CONNECTED     7729      
 unix  3      [ ]         STREAM     CONNECTED     7726     /tmp/orbit-eleanor/linc-550-0-1254175b29290  
 unix  3      [ ]         STREAM     CONNECTED     7725      
 unix  3      [ ]         STREAM     CONNECTED     7724     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     7723      
 unix  3      [ ]         STREAM     CONNECTED     7722     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7721      
 unix  3      [ ]         STREAM     CONNECTED     7718     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7717      
 unix  3      [ ]         STREAM     CONNECTED     7716     /tmp/orbit-eleanor/linc-550-0-1254175b29290  
 unix  3      [ ]         STREAM     CONNECTED     7715      
 unix  3      [ ]         STREAM     CONNECTED     7712     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7711      
 unix  3      [ ]         STREAM     CONNECTED     7709     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7708      
 unix  3      [ ]         STREAM     CONNECTED     7707     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     7706      
 unix  3      [ ]         STREAM     CONNECTED     7702     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7701      
 unix  3      [ ]         STREAM     CONNECTED     7697     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7696      
 unix  3      [ ]         STREAM     CONNECTED     7651     /tmp/orbit-eleanor/linc-54d-0-68597cbde2349  
 unix  3      [ ]         STREAM     CONNECTED     7650      
 unix  3      [ ]         STREAM     CONNECTED     7649     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7648      
 unix  3      [ ]         STREAM     CONNECTED     7646     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7645      
 unix  3      [ ]         STREAM     CONNECTED     7640     /tmp/orbit-eleanor/linc-54d-0-68597cbde2349  
 unix  3      [ ]         STREAM     CONNECTED     7639      
 unix  3      [ ]         STREAM     CONNECTED     7636     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     7635      
 unix  3      [ ]         STREAM     CONNECTED     7583     /tmp/orbit-eleanor/linc-543-0-7c9e9a43b68f4  
 unix  3      [ ]         STREAM     CONNECTED     7582      
 unix  3      [ ]         STREAM     CONNECTED     7581     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     7580      
 unix  3      [ ]         STREAM     CONNECTED     7577     /tmp/orbit-eleanor/linc-543-0-7c9e9a43b68f4  
 unix  3      [ ]         STREAM     CONNECTED     7576      
 unix  3      [ ]         STREAM     CONNECTED     7573     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7572      
 unix  3      [ ]         STREAM     CONNECTED     7570     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7569      
 unix  3      [ ]         STREAM     CONNECTED     7568     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     7567      
 unix  3      [ ]         STREAM     CONNECTED     7563     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7562      
 unix  3      [ ]         STREAM     CONNECTED     7239     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7238      
 unix  3      [ ]         STREAM     CONNECTED     7230     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7229      
 unix  3      [ ]         STREAM     CONNECTED     7227     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7226      
 unix  3      [ ]         STREAM     CONNECTED     7178     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     7177      
 unix  3      [ ]         STREAM     CONNECTED     7149     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7148      
 unix  3      [ ]         STREAM     CONNECTED     7070     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7069      
 unix  3      [ ]         STREAM     CONNECTED     7063     /tmp/orbit-eleanor/linc-504-0-252775a9ba5a9  
 unix  3      [ ]         STREAM     CONNECTED     7062      
 unix  3      [ ]         STREAM     CONNECTED     7059     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     7058      
 unix  3      [ ]         STREAM     CONNECTED     7053     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     7052      
 unix  3      [ ]         STREAM     CONNECTED     7050     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7049      
 unix  3      [ ]         STREAM     CONNECTED     6965     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6964      
 unix  3      [ ]         STREAM     CONNECTED     6951     /home/eleanor/.pulse/35841d8b96cc824cdf3c9f9e4d0e40de-runtime/native  
 unix  3      [ ]         STREAM     CONNECTED     6950      
 unix  3      [ ]         STREAM     CONNECTED     6941     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6940      
 unix  3      [ ]         STREAM     CONNECTED     6928     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6927      
 unix  3      [ ]         STREAM     CONNECTED     6914     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6913      
 unix  3      [ ]         STREAM     CONNECTED     6911     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6910      
 unix  3      [ ]         STREAM     CONNECTED     6896     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6895      
 unix  3      [ ]         STREAM     CONNECTED     6894     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6893      
 unix  3      [ ]         STREAM     CONNECTED     6890     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6889      
 unix  3      [ ]         STREAM     CONNECTED     6865     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6864      
 unix  3      [ ]         STREAM     CONNECTED     6861     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6860      
 unix  2      [ ]         DGRAM                    6855      
 unix  3      [ ]         STREAM     CONNECTED     6854     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6853      
 unix  3      [ ]         STREAM     CONNECTED     6849     /tmp/orbit-eleanor/linc-4e7-0-575a06f915e71  
 unix  3      [ ]         STREAM     CONNECTED     6848      
 unix  3      [ ]         STREAM     CONNECTED     6845     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6844      
 unix  3      [ ]         STREAM     CONNECTED     6816     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6815      
 unix  3      [ ]         STREAM     CONNECTED     6809     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6808      
 unix  3      [ ]         STREAM     CONNECTED     6778     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6777      
 unix  3      [ ]         STREAM     CONNECTED     6765     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6764      
 unix  3      [ ]         STREAM     CONNECTED     6762     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6761      
 unix  3      [ ]         STREAM     CONNECTED     6755     /tmp/orbit-eleanor/linc-4cf-0-2c4a27a8d593  
 unix  3      [ ]         STREAM     CONNECTED     6754      
 unix  3      [ ]         STREAM     CONNECTED     6751     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6750      
 unix  3      [ ]         STREAM     CONNECTED     6747     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6746      
 unix  3      [ ]         STREAM     CONNECTED     6707     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6706      
 unix  3      [ ]         STREAM     CONNECTED     6702     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6701      
 unix  3      [ ]         STREAM     CONNECTED     6690     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6689      
 unix  3      [ ]         STREAM     CONNECTED     6688     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6687      
 unix  3      [ ]         STREAM     CONNECTED     6686     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6685      
 unix  3      [ ]         STREAM     CONNECTED     6682     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6681      
 unix  3      [ ]         STREAM     CONNECTED     6680     /tmp/orbit-eleanor/linc-4bd-0-9db6d861d9cb  
 unix  3      [ ]         STREAM     CONNECTED     6679      
 unix  3      [ ]         STREAM     CONNECTED     6678     /tmp/orbit-eleanor/linc-4bd-0-9db6d861d9cb  
 unix  3      [ ]         STREAM     CONNECTED     6677      
 unix  3      [ ]         STREAM     CONNECTED     6676     /tmp/orbit-eleanor/linc-4bf-0-73454d1a19466  
 unix  3      [ ]         STREAM     CONNECTED     6675      
 unix  3      [ ]         STREAM     CONNECTED     6674     /tmp/orbit-eleanor/linc-4bf-0-73454d1a19466  
 unix  3      [ ]         STREAM     CONNECTED     6673      
 unix  3      [ ]         STREAM     CONNECTED     6672     /tmp/orbit-eleanor/linc-4c2-0-13b5d4cf1e004  
 unix  3      [ ]         STREAM     CONNECTED     6671      
 unix  3      [ ]         STREAM     CONNECTED     6670     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6669      
 unix  3      [ ]         STREAM     CONNECTED     6667     /tmp/orbit-eleanor/linc-4c2-0-13b5d4cf1e004  
 unix  3      [ ]         STREAM     CONNECTED     6666      
 unix  3      [ ]         STREAM     CONNECTED     6668     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6664      
 unix  3      [ ]         STREAM     CONNECTED     6665     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6663      
 unix  3      [ ]         STREAM     CONNECTED     6662     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6661      
 unix  3      [ ]         STREAM     CONNECTED     6660     /tmp/orbit-eleanor/linc-4be-0-27a018014b6f  
 unix  3      [ ]         STREAM     CONNECTED     6659      
 unix  3      [ ]         STREAM     CONNECTED     6658     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6657      
 unix  3      [ ]         STREAM     CONNECTED     6656     /tmp/orbit-eleanor/linc-4b7-0-16b47db210b43  
 unix  3      [ ]         STREAM     CONNECTED     6655      
 unix  3      [ ]         STREAM     CONNECTED     6652     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6651      
 unix  3      [ ]         STREAM     CONNECTED     6650     /tmp/orbit-eleanor/linc-4be-0-27a018014b6f  
 unix  3      [ ]         STREAM     CONNECTED     6649      
 unix  3      [ ]         STREAM     CONNECTED     6648     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6647      
 unix  3      [ ]         STREAM     CONNECTED     6645     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6644      
 unix  3      [ ]         STREAM     CONNECTED     6641     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6640      
 unix  3      [ ]         STREAM     CONNECTED     6639     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6638      
 unix  3      [ ]         STREAM     CONNECTED     6637     /tmp/orbit-eleanor/linc-4b7-0-16b47db210b43  
 unix  3      [ ]         STREAM     CONNECTED     6636      
 unix  3      [ ]         STREAM     CONNECTED     6635     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6634      
 unix  3      [ ]         STREAM     CONNECTED     6631     /tmp/orbit-eleanor/linc-4c2-0-13b5d4cf1e004  
 unix  3      [ ]         STREAM     CONNECTED     6629      
 unix  3      [ ]         STREAM     CONNECTED     6626     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6625      
 unix  3      [ ]         STREAM     CONNECTED     6642     /tmp/orbit-eleanor/linc-4bd-0-9db6d861d9cb  
 unix  3      [ ]         STREAM     CONNECTED     6624      
 unix  3      [ ]         STREAM     CONNECTED     6621     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6620     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6619      
 unix  3      [ ]         STREAM     CONNECTED     6618      
 unix  3      [ ]         STREAM     CONNECTED     6633     /tmp/orbit-eleanor/linc-4bf-0-73454d1a19466  
 unix  3      [ ]         STREAM     CONNECTED     6617      
 unix  3      [ ]         STREAM     CONNECTED     6614     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6613      
 unix  3      [ ]         STREAM     CONNECTED     6609     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6608      
 unix  3      [ ]         STREAM     CONNECTED     6610     /tmp/orbit-eleanor/linc-4be-0-27a018014b6f  
 unix  3      [ ]         STREAM     CONNECTED     6604      
 unix  3      [ ]         STREAM     CONNECTED     6601     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6600      
 unix  3      [ ]         STREAM     CONNECTED     6630     /tmp/orbit-eleanor/linc-4c3-0-14002182d179  
 unix  3      [ ]         STREAM     CONNECTED     6599      
 unix  3      [ ]         STREAM     CONNECTED     6598     /tmp/orbit-eleanor/linc-4c3-0-14002182d179  
 unix  3      [ ]         STREAM     CONNECTED     6597      
 unix  3      [ ]         STREAM     CONNECTED     6596     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6595      
 unix  3      [ ]         STREAM     CONNECTED     6593     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6592      
 unix  3      [ ]         STREAM     CONNECTED     6605     /tmp/orbit-eleanor/linc-4b7-0-16b47db210b43  
 unix  3      [ ]         STREAM     CONNECTED     6589      
 unix  3      [ ]         STREAM     CONNECTED     6586     /tmp/orbit-eleanor/linc-4c3-0-14002182d179  
 unix  3      [ ]         STREAM     CONNECTED     6585      
 unix  3      [ ]         STREAM     CONNECTED     6584     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6583      
 unix  3      [ ]         STREAM     CONNECTED     6580     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6579      
 unix  3      [ ]         STREAM     CONNECTED     6549     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6545      
 unix  3      [ ]         STREAM     CONNECTED     6548     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6544      
 unix  3      [ ]         STREAM     CONNECTED     6546     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6543      
 unix  3      [ ]         STREAM     CONNECTED     6541     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6539      
 unix  3      [ ]         STREAM     CONNECTED     6540     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6534      
 unix  3      [ ]         STREAM     CONNECTED     6291     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6290      
 unix  3      [ ]         STREAM     CONNECTED     6254     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     6253      
 unix  3      [ ]         STREAM     CONNECTED     6251     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6250      
 unix  3      [ ]         STREAM     CONNECTED     6249     /tmp/orbit-eleanor/linc-4ae-0-7977b4924d802  
 unix  3      [ ]         STREAM     CONNECTED     6248      
 unix  3      [ ]         STREAM     CONNECTED     6246     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6245      
 unix  3      [ ]         STREAM     CONNECTED     6240     /tmp/orbit-eleanor/linc-4b1-0-30255ae846e9d  
 unix  3      [ ]         STREAM     CONNECTED     6239      
 unix  3      [ ]         STREAM     CONNECTED     6236     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6235      
 unix  3      [ ]         STREAM     CONNECTED     6229     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6228      
 unix  3      [ ]         STREAM     CONNECTED     6225     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6224      
 unix  3      [ ]         STREAM     CONNECTED     6177     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     6176      
 unix  3      [ ]         STREAM     CONNECTED     6173     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6172      
 unix  3      [ ]         STREAM     CONNECTED     6167     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6166      
 unix  3      [ ]         STREAM     CONNECTED     6161     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6160      
 unix  3      [ ]         STREAM     CONNECTED     6147     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6146      
 unix  3      [ ]         STREAM     CONNECTED     6145     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6144      
 unix  3      [ ]         STREAM     CONNECTED     6129     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6128      
 unix  3      [ ]         STREAM     CONNECTED     6122     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6121      
 unix  3      [ ]         STREAM     CONNECTED     6094     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6093      
 unix  3      [ ]         STREAM     CONNECTED     6090     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6089      
 unix  3      [ ]         STREAM     CONNECTED     6086     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6085      
 unix  3      [ ]         STREAM     CONNECTED     6080     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6079      
 unix  3      [ ]         STREAM     CONNECTED     6069     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6068      
 unix  3      [ ]         STREAM     CONNECTED     6062     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6061      
 unix  3      [ ]         STREAM     CONNECTED     6060     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6059      
 unix  3      [ ]         STREAM     CONNECTED     6054     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6053      
 unix  3      [ ]         STREAM     CONNECTED     6048     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6047      
 unix  3      [ ]         STREAM     CONNECTED     6035     /tmp/orbit-eleanor/linc-46f-0-6d21f7889d303  
 unix  3      [ ]         STREAM     CONNECTED     6034      
 unix  3      [ ]         STREAM     CONNECTED     6030     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6029      
 unix  3      [ ]         STREAM     CONNECTED     6024     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6023      
 unix  3      [ ]         STREAM     CONNECTED     6022     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     6021      
 unix  3      [ ]         STREAM     CONNECTED     6020     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6019      
 unix  3      [ ]         STREAM     CONNECTED     6015     /tmp/orbit-eleanor/linc-471-0-67ac7c9c8dd42  
 unix  3      [ ]         STREAM     CONNECTED     6014      
 unix  3      [ ]         STREAM     CONNECTED     6011     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6010      
 unix  3      [ ]         STREAM     CONNECTED     6009     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     6008      
 unix  3      [ ]         STREAM     CONNECTED     6001     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6000      
 unix  3      [ ]         STREAM     CONNECTED     5998     /tmp/orbit-eleanor/linc-46d-0-aefa4007e7c2  
 unix  3      [ ]         STREAM     CONNECTED     5994      
 unix  3      [ ]         STREAM     CONNECTED     5991     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5990      
 unix  3      [ ]         STREAM     CONNECTED     5986     /tmp/orbit-eleanor/linc-472-0-1188f1da7ad70  
 unix  3      [ ]         STREAM     CONNECTED     5985      
 unix  3      [ ]         STREAM     CONNECTED     5982     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5981      
 unix  3      [ ]         STREAM     CONNECTED     5978     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5977      
 unix  3      [ ]         STREAM     CONNECTED     5973     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5972      
 unix  3      [ ]         STREAM     CONNECTED     5971     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5970      
 unix  3      [ ]         STREAM     CONNECTED     5968     /tmp/orbit-eleanor/linc-46b-0-32b6295e6336b  
 unix  3      [ ]         STREAM     CONNECTED     5967      
 unix  3      [ ]         STREAM     CONNECTED     5961     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5960      
 unix  3      [ ]         STREAM     CONNECTED     5963     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5959      
 unix  3      [ ]         STREAM     CONNECTED     5964     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5958      
 unix  3      [ ]         STREAM     CONNECTED     5956     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5955      
 unix  3      [ ]         STREAM     CONNECTED     5954     /tmp/orbit-eleanor/linc-46e-0-cd9483f4b8c0  
 unix  3      [ ]         STREAM     CONNECTED     5953      
 unix  3      [ ]         STREAM     CONNECTED     5950     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5949      
 unix  3      [ ]         STREAM     CONNECTED     5948     /home/eleanor/.pulse/35841d8b96cc824cdf3c9f9e4d0e40de-runtime/native  
 unix  3      [ ]         STREAM     CONNECTED     5947      
 unix  3      [ ]         STREAM     CONNECTED     5944     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5943      
 unix  3      [ ]         STREAM     CONNECTED     5941     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5940      
 unix  3      [ ]         STREAM     CONNECTED     5939     /tmp/orbit-eleanor/linc-476-0-5b97fc503c24e  
 unix  3      [ ]         STREAM     CONNECTED     5937      
 unix  3      [ ]         STREAM     CONNECTED     5934     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5933      
 unix  3      [ ]         STREAM     CONNECTED     5926     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5925      
 unix  3      [ ]         STREAM     CONNECTED     5922     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5920      
 unix  2      [ ]         DGRAM                    5872      
 unix  3      [ ]         STREAM     CONNECTED     5871     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5870      
 unix  3      [ ]         STREAM     CONNECTED     5866     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5865      
 unix  3      [ ]         STREAM     CONNECTED     5864     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5863      
 unix  3      [ ]         STREAM     CONNECTED     5861     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5860      
 unix  3      [ ]         STREAM     CONNECTED     5857     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5856      
 unix  3      [ ]         STREAM     CONNECTED     5854     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5853      
 unix  3      [ ]         STREAM     CONNECTED     5850     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5849      
 unix  3      [ ]         STREAM     CONNECTED     5848     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5847      
 unix  3      [ ]         STREAM     CONNECTED     5834     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5833      
 unix  3      [ ]         STREAM     CONNECTED     5832     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5831      
 unix  3      [ ]         STREAM     CONNECTED     5550     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5549      
 unix  3      [ ]         STREAM     CONNECTED     5548     /tmp/orbit-eleanor/linc-46a-0-7c66b76f9cc94  
 unix  3      [ ]         STREAM     CONNECTED     5547      
 unix  3      [ ]         STREAM     CONNECTED     5544     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5543      
 unix  3      [ ]         STREAM     CONNECTED     5540     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5539      
 unix  3      [ ]         STREAM     CONNECTED     5536     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5535      
 unix  3      [ ]         STREAM     CONNECTED     5528     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5527      
 unix  3      [ ]         STREAM     CONNECTED     5526     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5525      
 unix  3      [ ]         STREAM     CONNECTED     5514     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5513      
 unix  3      [ ]         STREAM     CONNECTED     5479     @/tmp/.ICE-unix/1058  
 unix  3      [ ]         STREAM     CONNECTED     5478      
 unix  3      [ ]         STREAM     CONNECTED     5476     /tmp/orbit-eleanor/linc-45f-0-53d6c5eb5e3b9  
 unix  3      [ ]         STREAM     CONNECTED     5475      
 unix  3      [ ]         STREAM     CONNECTED     5472     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5471      
 unix  3      [ ]         STREAM     CONNECTED     5467     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5466      
 unix  3      [ ]         STREAM     CONNECTED     5463     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5462      
 unix  3      [ ]         STREAM     CONNECTED     5458     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5457      
 unix  3      [ ]         STREAM     CONNECTED     5436     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5435      
 unix  2      [ ]         DGRAM                    5434      
 unix  3      [ ]         STREAM     CONNECTED     5423     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5422      
 unix  3      [ ]         STREAM     CONNECTED     5353     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5352      
 unix  3      [ ]         STREAM     CONNECTED     5348     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5347      
 unix  3      [ ]         STREAM     CONNECTED     5309     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5308      
 unix  3      [ ]         STREAM     CONNECTED     5303     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5302      
 unix  3      [ ]         STREAM     CONNECTED     5299     /tmp/orbit-eleanor/linc-454-0-4baead3caaf3b  
 unix  3      [ ]         STREAM     CONNECTED     5298      
 unix  3      [ ]         STREAM     CONNECTED     5295     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5294      
 unix  3      [ ]         STREAM     CONNECTED     5288     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5287      
 unix  3      [ ]         STREAM     CONNECTED     5285     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     5284      
 unix  3      [ ]         STREAM     CONNECTED     5257     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     5256      
 unix  3      [ ]         STREAM     CONNECTED     5142     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5141      
 unix  3      [ ]         STREAM     CONNECTED     5139     /tmp/orbit-eleanor/linc-422-0-2c207fbd568ef  
 unix  3      [ ]         STREAM     CONNECTED     5138      
 unix  3      [ ]         STREAM     CONNECTED     5135     /tmp/orbit-eleanor/linc-44b-0-22d45d77471d0  
 unix  3      [ ]         STREAM     CONNECTED     5134      
 unix  3      [ ]         STREAM     CONNECTED     5131     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5130      
 unix  3      [ ]         STREAM     CONNECTED     4900     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     4899      
 unix  3      [ ]         STREAM     CONNECTED     4859     @/tmp/dbus-x2xU2pKFBp  
 unix  3      [ ]         STREAM     CONNECTED     4858      
 unix  3      [ ]         STREAM     CONNECTED     4856     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4855      
 unix  3      [ ]         STREAM     CONNECTED     4852     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4851      
 unix  3      [ ]         STREAM     CONNECTED     4850      
 unix  3      [ ]         STREAM     CONNECTED     4849      
 unix  3      [ ]         STREAM     CONNECTED     4838     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4837      
 unix  3      [ ]         STREAM     CONNECTED     4698     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     4697      
 unix  2      [ ]         DGRAM                    4690      
 unix  3      [ ]         STREAM     CONNECTED     4689     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4688      
 unix  3      [ ]         STREAM     CONNECTED     4684     @/tmp/gdm-session-HoVxjucK  
 unix  3      [ ]         STREAM     CONNECTED     4683      
 unix  3      [ ]         STREAM     CONNECTED     4680     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     4679      
 unix  3      [ ]         STREAM     CONNECTED     4613     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     4612      
 unix  2      [ ]         DGRAM                    3921      
 unix  2      [ ]         DGRAM                    3909      
 unix  3      [ ]         STREAM     CONNECTED     3851     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3850      
 unix  2      [ ]         DGRAM                    3849      
 unix  3      [ ]         STREAM     CONNECTED     3820     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3819      
 unix  2      [ ]         DGRAM                    3793      
 unix  3      [ ]         STREAM     CONNECTED     3750     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3749      
 unix  3      [ ]         STREAM     CONNECTED     3712     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3711      
 unix  3      [ ]         STREAM     CONNECTED     3640     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3639      
 unix  2      [ ]         DGRAM                    3561      
 unix  2      [ ]         DGRAM                    3560      
 unix  3      [ ]         STREAM     CONNECTED     3554     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3553      
 unix  3      [ ]         STREAM     CONNECTED     3550     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3549      
 unix  3      [ ]         STREAM     CONNECTED     3531     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3530      
 unix  3      [ ]         STREAM     CONNECTED     3523      
 unix  3      [ ]         STREAM     CONNECTED     3522      
 unix  3      [ ]         STREAM     CONNECTED     3496     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3495      
 unix  3      [ ]         STREAM     CONNECTED     3473     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     3472      
 unix  3      [ ]         STREAM     CONNECTED     3471      
 unix  3      [ ]         STREAM     CONNECTED     3470      
 unix  3      [ ]         DGRAM                    2719      
 unix  3      [ ]         DGRAM                    2718      
 unix  3      [ ]         STREAM     CONNECTED     2665     @/com/ubuntu/upstart  
 unix  3      [ ]         STREAM     CONNECTED     2664      
 tom@eleanor-laptop:~$ 



I followed that up with the pinging, and here are the results:-
Version:1.0 StartHTML:0000000167 EndHTML:0000001079 StartFragment:0000000454 EndFragment:0000001063    	 	 	 	p { margin-bottom: 0.21cm; }  tom@eleanor-laptop:~$ ping c5 [www.bbc.co.uk](www.bbc.co.uk)  
 ping: unknown host c5  
 tom@eleanor-laptop:~$  
 tom@eleanor-laptop:~$ wget [http://www.bbc.co.uk](http://www.bbc.co.uk)  
 --2011-01-06 12:46:55--  [http://www.bbc.co.uk/](http://www.bbc.co.uk/)  
 Resolving [www.bbc.co.uk](www.bbc.co.uk)... failed: Name or service not known.  
 wget: unable to resolve host address `[www.bbc.co.uk](www.bbc.co.uk)'  
 tom@eleanor-laptop:~$ 



The problem seems random in relation to when it happens. It is hard to recall a time when I could not access the first site I asked for. Usually it happens when I have abour 3 tabs up and running. Today, I thought it was not going to happen at all, just to spite me, but it did happen after hammering the sites on about 5 tabs for a couple of minutes ... that was when I did the pinging and BBc was one of the sites that was tabbed at the time.


Good luck with this.
Is anybody watching this thread? Situation remains unchanged. After a couple of minutes and a few tabs, Firefox simply does not load sites. Then the blue bar, bottom right of the browser window, isn't blue, and does not move.

Would it be worth re-installing Firefox?

Jock

---

### Post by dandnsmith on 2011-01-08
If you've reached the desperation point, why not reinstall FF.
Don't forget to wipe any customisation, as that could harbour problems.

Good luck

---

### Post by lovinglinux on 2011-01-08
[http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

---

### Post by jock mackay on 2011-01-08
> **lovinglinux said:**
> [http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)
I got this failure in the Firefox error console, but I do not know how to interpret it. I hope someone can.

Version:1.0 StartHTML:0000000167 EndHTML:0000001050 StartFragment:0000000454 EndFragment:0000001034    	 	 	 	p { margin-bottom: 0.21cm; }  Error: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIXMLHttpRequest.statusText]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "JS frame :: file:///usr/lib/firefox-3.6.13/components/nsBlocklistService.js :: anonymous :: line 469"  data: no]
 Source File: file:///usr/lib/firefox-3.6.13/components/nsBlocklistService.js
 Line: 469


Scotty

---

### Post by speedwell68 on 2011-01-08
Might I suggest that you try swapping the network manager you use.  I had a similar sounding problem when using a BT Home Hub with my Uncle's laptop.  In the end, out of frustration, I changed the network manager from network-manager-gnome to wicd and the problem went away.  Basically go into the Synaptic package manager and deselect the network-manager-gnome package and select wicd.

---

### Post by lovinglinux on 2011-01-08
Go to the Security tab in FF preferences and disable the options to block web forgeries and attack sites.

Disable all extensions and plugins if the above doesn't help.

---

### Post by jock mackay on 2011-01-08
Progress I think. I have not done what Speedwell ssuggested yet. However I have done everything in the post from lovinglinux. Everything was working beautifully until I reached a site which asked for the java plugin, so I enabled jave(TM) Plug-in 1.6.0_23, and my problems returned immediately. I see that I have java 6.0 plug in installed on the computer, and that seems to come with JRE, although I do not see it at the moment.
Does that help?

---

### Post by lovinglinux on 2011-01-08
> **jock mackay said:**
> Progress I think. I have not done what Speedwell ssuggested yet. However I have done everything in the post from lovinglinux. Everything was working beautifully until I reached a site which asked for the java plugin, so I enabled jave(TM) Plug-in 1.6.0_23, and my problems returned immediately. I see that I have java 6.0 plug in installed on the computer, and that seems to come with JRE, although I do not see it at the moment.
Does that help?

Switch between sun-java6-plugin and icedtea6-plugin.

---

### Post by jock mackay on 2011-01-09
Because of an earlir problem, I uninstalled icedtea. Before reinstalling that , would it make sense to try to get the Java 6 plug in working in Firefox rather than the 1.6.0_23 version?

---

### Post by jock mackay on 2011-01-09
> **lovinglinux said:**
> Switch between sun-java6-plugin and icedtea6-plugin.
I thought I had isolated this issue to a java problem. However today whern I enabled Shockwave in oder to watch a video clip, that almost immediately brought the inability to connect to server problem back.

Disabling Shockwave go Firefox up and running again.

Grrrrrrrrrrr

---

### Post by lovinglinux on 2011-01-09
> **jock mackay said:**
> I thought I had isolated this issue to a java problem. However today whern I enabled Shockwave in oder to watch a video clip, that almost immediately brought the inability to connect to server problem back.

Disabling Shockwave go Firefox up and running again.

Grrrrrrrrrrr

So you have a generalized plugin issue. I have no idea how to solve this problem. Perhaps you should try to re-install and report the problem to Mozilla and Canonical developers.

---

### Post by jock mackay on 2011-01-09
> **lovinglinux said:**
> So you have a generalized plugin issue. I have no idea how to solve this problem. Perhaps you should try to re-install and report the problem to Mozilla and Canonical developers.
Thanks for all your input, lovinglinux. Looks like the end for this issue. I will have a think about how to move on from here.
Jock

---

### Post by lovinglinux on 2011-01-09
> **jock mackay said:**
> Thanks for all your input, lovinglinux. Looks like the end for this issue. I will have a think about how to move on from here.
Jock

Try downloading Firefox 4 from Mozilla and check if you experience the same issue.

---

