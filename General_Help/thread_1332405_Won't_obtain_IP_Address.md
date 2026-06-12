---
title: "Won't obtain IP Address"
date: 2009-11-20
forum: General Help
---

### Post by prem1er on 2009-11-20
Had trouble last night obtaining an IP address on my 9.10 machine. Both wired and wireless wouldn't pick up an IP address. Using WICD network manager. I removed the password from the wireless and still no success. Logged onto XP with the same machine and had no trouble. I haven't seen this before. Does anyone know what the problem could be.  The error on WICD was "Could not obtain IP adress." TIA.

---

### Post by prem1er on 2009-11-20
bump

---

### Post by dddanmar on 2009-11-20
OK, 

does

```
ifconfig
```

show any devices listed?

Is there any visual cues when you plug/unplug the cable from GNOME?
If you click on the network manager are there any devices listed?
Output of /var/log files when you plug/unplug the cable?

---

### Post by Iowan on 2009-11-20
Different version, but just in case...
[http://ubuntuforums.org/showthread.php?t=1156441]("http://ubuntuforums.org/showthread.php?t=1156441")

---

### Post by neerajadsul on 2009-11-20
I don't think if you need to use WICD. Ubuntu has inbuilt network manager which should work without any problem (at least for wired connection). Did you try without WICD?

---

### Post by Ancanus on 2009-11-20
Do a  ```
tail /var/log/wicd/wicd.log
```

---

### Post by mo.reina on 2009-11-20
try connecting manually through the terminal

```
sudo iwconfig essid "*name of wireless connection here*" channel *channel here, usually 6, can check through ifconfig command* mode managed key off
sudo dhclient
```

or for a wired connection just
```
sudo dhclient
```

---

### Post by a-web on 2009-11-24
I got a similar problem.  I had been fine with wireless networks, but after trying to get on a WPA2 network all wireless is having issues.  Now I cannot reliably connect to open networks and often get "Connection Failed:  Unable to Get IP Address".

(Running Karmic on a Compac Presario 2100.)

From```
tail/var/log/wicd/wicd.log
```I get```
2009/11/24 15:13:43 :: DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 8
2009/11/24 15:13:51 :: DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 14
2009/11/24 15:14:05 :: DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 9
2009/11/24 15:14:14 :: DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 20
2009/11/24 15:14:34 :: DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 10
2009/11/24 15:14:44 :: No DHCPOFFERS received
2009/11/24 15:14:44 :: No working leases in persistent database - sleeping.
2009/11/24 15:14:54 :: DHCP connection failed
2009/11/24 15:14:54 :: Sending connection attempt result dhcp_failed
```I am open to assistance...

---

### Post by prem1er on 2009-11-24
> **neerajadsul said:**
> I don't think if you need to use WICD. Ubuntu has inbuilt network manager which should work without any problem (at least for wired connection). Did you try without WICD?

I got rid of the network manager, because WICD seemed to work better on my home network. I was having trouble on my friends network. I did not try the built in network manager on the network where I was having trouble.

---

### Post by prem1er on 2009-11-24
I won't be able to test the suggestions until tomorrow when I will be back on that network. I will post then. Thanks everyone.

---

### Post by Agent Smith on 2009-11-24
I had the same problem with not connecting to my wireless network. I had to manualy type in the ip address and it connects fine everytime. you can do this by choosing edit connections in the network manager.

---

### Post by prem1er on 2009-11-30
> **Ancanus said:**
> Do a  ```
tail /var/log/wicd/wicd.log
```

Hey, just got back to do some test on this network.  Here is the output of the log file while it is trying to connect.

```
2009/11/29 16:01:47 :: 
2009/11/29 16:01:48 :: Listening on LPF/wlan0/
2009/11/29 16:01:48 :: Sending on   LPF/wlan0/
2009/11/29 16:01:48 :: Sending on   Socket/fallback
2009/11/29 16:01:50 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
2009/11/29 16:01:55 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2009/11/29 16:02:02 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
2009/11/29 16:02:15 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2009/11/29 16:02:29 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
2009/11/29 16:02:42 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2009/11/29 16:02:50 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
2009/11/29 16:02:51 :: No DHCPOFFERS received.
2009/11/29 16:02:51 :: No working leases in persistent database - sleeping.
2009/11/29 16:02:59 :: DHCP connection failed
2009/11/29 16:02:59 :: exiting connection thread
2009/11/29 16:03:00 :: Sending connection attempt result dhcp_failed
```

---

### Post by prem1er on 2009-11-30
> **mo.reina said:**
> try connecting manually through the terminal

```
sudo iwconfig essid "*name of wireless connection here*" channel *channel here, usually 6, can check through ifconfig command* mode managed key off
sudo dhclient
```

or for a wired connection just
```
sudo dhclient
```


I get the same errors when I try to connect manually. It tries a DHCPDISCOVER and then says...

```
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

```

I know the router has enough addresses available, so I still can't figure out why this is happening.

---

### Post by prem1er on 2009-11-30
> **Iowan said:**
> Different version, but just in case...
[http://ubuntuforums.org/showthread.php?t=1156441]("http://ubuntuforums.org/showthread.php?t=1156441")

> **Iowan said:**
> [Updated update] Per a suggestion in another [thread]("http://ubuntuforums.org/showpost.php?p=7276275&postcount=8"), I tried commenting out the "option rfc3442" line and removing the reference in the "request" line - rebooted, and got a DHCP address.  (Thanks Peter09) We'll see if the "fix" stays fixed...

It should be noted that the actual path is /etc/dhcp3/dhclient.conf. That got edited a couple of posts later than the one I linked.

I tried the fix you posted. And still no luck after the restart. Same errors in the WICD log file.  Here is what my /etc/dhcp3/dhclient.conf file looks like. Let me know if you see anything incorrect.

```
# Configuration file for /sbin/dhclient, which is included in Debian's

# option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
        ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

