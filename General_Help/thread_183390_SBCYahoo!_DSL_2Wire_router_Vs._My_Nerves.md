---
title: "SBC/Yahoo! DSL 2Wire router Vs. My Nerves"
date: 2006-05-27
forum: General Help
---

### Post by jim_mule on 2006-05-27
hello fine peoples of the ubuntu forums.
its my first time posting, because its the first time i couldnt find the solution here already.
so heres the problem:
my family has purchased a new 2wire router with Yahoo! SBC DSL.
it works fine under windows, but i am trying to ween them onto linux, namely ubuntu.
i have tried: dhclient, dhclient3, rp-pppoe-3.8, pppoeconf, and many variations of manually configuring my ip address/gateway/resolv.conf/ and trying to ping the router/or going to it via firefox. i have also tried kanotix livedcd, no luck there either.
anyone dealt with this?

---

### Post by skyshark88 on 2006-05-27
Dude try his yet...[http://www.obviously.com/tech_tips/Yahoo_DSL_setup_no_CD.html](http://www.obviously.com/tech_tips/Yahoo_DSL_setup_no_CD.html)

---

### Post by RRS on 2006-05-27
Do you have Ubuntu on a seperate computer or are you dual-booting?

Either way, first in Windows open the command line from the start menu>run>cmd. Type "ipconfig\all" (without quotes)

The readout from this should give the default gateway and  DHCP servers IP address, likely the same. This is the IP of your modem/router (likely 192.168.1.254).

Now back to Ubuntu;
System>Administration>Network Settings
Select DNS and next to Network Servers; "add"
In the box enter the modem/routers IP address. Now down to the Search Domains, again "add" and here try "gateway.2wire.net". That's what I have in mine and it should be generic to the brand.

Now select the Connections tab and eth0>properties.
Under configuration select DHCP from the dropdown menu and check the box for "enable this connection" followed by "OK". I can't remember if this will activate etho, if not "activate" before "OK" again to close network settings.

You should now be online, if not post back with the results from "ipconfig\all" in windows along with "ifconfig" from Ubuntu.

---

### Post by jim_mule on 2006-05-27
im afraid it is still no success.
some more info: im using a wire, its not wireless, and it is a dual boot machine, it is the only one ocnnected to the 2wire box.
here is ipconfig /all:
```

Windows IP Configuration

        Host Name . . . . . . . . . . . . : YOUR-D0F3A2C7CE
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : gateway.2wire.net

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : gateway.2wire.net
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-16-17-31-DE-49
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.64
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254
        DHCP Server . . . . . . . . . . . : 192.168.1.254
        DNS Servers . . . . . . . . . . . : 192.168.1.254
        Lease Obtained. . . . . . . . . . : Saturday, May 27, 2006 9:24:24 PM
        Lease Expires . . . . . . . . . . : Sunday, May 28, 2006 9:24:24 PM

```

and here is ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:31:DE:49  
          inet6 addr: fe80::216:17ff:fe31:de49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:22 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080 (1.0 KiB)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)


```

---

### Post by RRS on 2006-05-28
Okay, I compared your ifconfig to mine and only spotted one difference, mine has; ```
inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
``` between the lines ```
Link encap:Ethernet  HWaddr 00:16:17:31:DE:49
``` and ```
inet6 addr: fe80::216:17ff:fe31:de49/64 Scope:Link
```

Have you tried to ping the modem @ 192.164.1.254? If that's succesful try accessing the modems setup interface from Firefox using the IP in the address bar, though since Windows connects ok I doubt anything needs to be changed there.

If pinging fails then try 
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

Another possibility is the nic driver, not sure if Nvidia drivers are installed. That subject seems well covered in [this thread]("http://www.ubuntuforums.org/showthread.php?t=87643").

Another thing that worked for me once when my router decided to quit talking to my ethernet card was to turn off the computer and unplug both the modem and the router, then power back up, doubt your situations the same but my ifconfig output was similar at the time.

Sorry for the delay but I had to dig out some old notes.
Hope some of this helps.

---

### Post by jim_mule on 2006-05-28
i tired all of the above, still no luck. i know that it is supposed to be a PPPoe type of connection, but nothing seems to work for that. and i would think a simple DHCP would do as well.

tried some more things i found online, from changing the hardware address in linux [someone said that the 2wire does not like dual-boots due to MAC addresses, something like that], to reseting it to factory settings then booting into linux, and still nothing works, also tried installing dhcpd, and using it instead of dhclient/dhclient3 and that did nothing either.

---

### Post by RRS on 2006-05-28
Hmm, I also have SBCYahoo and am using the provided 2wire modem (1070-B Gateway) which is also a router, though it it only has one connection port.

The only setup/connection problems I had were installing a Linksys router so I could connect 2 machines.

DId you have everything working in Windows before installing Ubuntu? The reason I ask is that I did and DHCP was detected and enabled during the Ubuntu installation on both of my machines with the modem turned on and connected, nothing extra for me to do afterwards.

For comparison purposes here's ```
 cat /etc/network/interfaces

```
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
iface eth0 inet dhcp
auto eth0

```

and my ifconfig;```
eth0      Link encap:Ethernet  HWaddr 00:12:17:52:A2:F2
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe52:a2f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:273658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:271298928 (258.7 MiB)  TX bytes:11507757 (10.9 MiB)
          Interrupt:209 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0ipconfig\all
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:168 (168.0 b)  TX bytes:168 (168.0 b)

```

I had to change several settings in the modem to enable use of the Linksys router so I doubt anything there would be of use to you. I seem to recall originally only having entered my SBCYahoo username and password beyond the default settings though before I got tired of manually switching the cable between computers.

> tried some more things i found online, from changing the hardware address in linux [someone said that the 2wire does not like dual-boots due to MAC addresses, something like that],

News to me and don't quite understand how dual boot would affect the MAC as it's hardware related.

I suspect the problem may be with your ethernet cards driver. Have you had a chance to check the link in my second post?

There's a lot of people here with more experience then me so let us know how things are (or aren't) progressing.

---

### Post by jim_mule on 2006-05-28
writing from ubuntu:
yeas it was the driver, the forcedeth driver or soemthing like this, its an opensource driver for the nforce chipset, and i installed nvidias driver, and did one simple dhclient, and then everything worked. 
many thanks to those who wrangled with this a bit as well.
i was really wondering why some people claimed they just used dhclient, and i was finding that quite frustrating, always satisfying to figure out the bug though, like beating the irritating boss in an NES game.

---

### Post by RRS on 2006-05-28
Congratulations and welcome :)

---

