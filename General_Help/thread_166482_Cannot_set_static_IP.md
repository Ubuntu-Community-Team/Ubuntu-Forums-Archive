---
title: "Cannot set static IP"
date: 2006-04-26
forum: General Help
---

### Post by spaceghoti on 2006-04-26
My Kubuntu box is able to connect to my Internet connection and see other computers on my LAN, but ifconfig eth0 won't register my IP address, either DHCP or static.  To finally get DHCP working correctly I added this to my startup:

```
# force DHCP
sudo dhclient
```

I have two versions of /etc/network/interfaces.  The one I'm currently trying to use is for static IP:

```
# netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
kurgan@Linus:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
# address 127.0.0.1
# netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address *.*.*.86
        netmask 255.255.255.0
        network *.*.*.0
        broadcast *.*.*.255
        gateway *.*.*.1
        dns-nameservers 204.127.203.135 216.214.225.135
```

The second is for DHCP:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
# address 127.0.0.1
# netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
```

Neither file seems to work, so I have to force DHCP through the first script.

Can anyone help me figure out why I can't get Kubuntu to recognize and use my static IP?

Thank you.

---

### Post by nanotube on 2006-04-26
have you tried editing /etc/dhcp3/dhclient.conf ? it has a bunch of options for overriding things, etc...

---

### Post by spaceghoti on 2006-04-26
Yes, everything is commented out except ```
send host-name "linus";
```

---

### Post by spaceghoti on 2006-05-02
Hello?  Does anyone have any ideas?  I'm working with a Linksys router, the latest G class wireless that I bought last September.  I'm connecting through a LAN cable on the built-in port in my Compaq Evo N610c.  Setting static IP used to work fine with Fedora Core 4.

---

### Post by kzutter on 2006-05-03
Doesn't the KDE "Network Settings" dialog of "System Settings" work?

Be sure to set your gateway under "Routes"

---

### Post by spaceghoti on 2006-05-03
[QUOTE=kzutter]Doesn't the KDE "Network Settings" dialog of "System Settings" work?

Be sure to set your gateway under "Routes"[/QUOTE]
It doesn't, sadly.  Trying to set a static IP through KNetworkConf usually just shut down my ethernet access.  I get IP 169.254.186.145 with netmask 255.255.0.0 after I apply and enable static IP, even when manually setting the gateway, route and DNS.  At that point, my network connection goes away.

---

### Post by Al3xanR0 on 2006-05-03
You are getting an APIPA (Automatic Private Internet Protocol Address) address  169.254.186.145  in Kubuntu that is odd??? An IP address beginning with  169.254 is usually rendered to windows workstations when they are unable to receive dhcp assignments from DHCP Servers.

---

### Post by spaceghoti on 2006-05-03
I swear, this laptop has been unsullied by anything Microsoft for almost a year.

---

### Post by kzutter on 2006-05-04
Sorry, I am late getting back to you.
Here is my interfaces file.

I successfully use a static ip and eth0 is activated automatically at boot.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
address 192.168.01.2
netmask 255.255.255.0
gateway 192.168.001.1

auto eth0

# The zd1211 network interface
iface wlan0 inet dhcp
#address 192.168.01.22
#netmask 255.255.255.0
#gateway 192.168.001.1
```

Also a question - Do you have a Microsoft box on the network that is set for "Internet Connection Sharing"?

---

### Post by spaceghoti on 2006-05-08
[QUOTE=kzutter]Sorry, I am late getting back to you.[/QUOTE]Hey, no problem.  I know how it is.

[snip]

> Also a question - Do you have a Microsoft box on the network that is set for "Internet Connection Sharing"?No, none of the Microsoft boxes on the network are using Internet Connection Sharing.  It's just five computers and two Linksys routers, one Wireless and one not.  The Wireless router is the gateway to the cable modem.

I'll try your configuration file and let you know how it goes.  Thank you!

---

### Post by spaceghoti on 2006-05-08
Unfortunately, your configuration file didn't work for me, with or without nameserver addresses.

I see resolvconf running before it tries to bring up network interfaces.  Anybody familiar with it?   Could some configuration there be responsible?

---

### Post by spaceghoti on 2006-05-11
Hello?  Anybody?  Any ideas?  Please?

---

### Post by spaceghoti on 2006-05-17
Still searching...

---

### Post by Directrix1 on 2006-05-17
resolvconf only sets up your resolv.conf file for dns lookups.  I too am interested in the solution to this because I am having the same problem (setup for a static IP, but am getting the 169.254. crap).  What kind of network card you have?  I'm using the e1000 driver for mine on AMD64.

---

### Post by spaceghoti on 2006-05-17
It's a Compaq EVO N610c laptop; I don't know if Compaq does their usual BS with ethernet cards in them but a quick Google search says they do fine with a eepro100 driver.

---

### Post by nexus_6 on 2006-08-13
i am having the exact same problem, neither DHCP nor Static IPs are shown correctly in ifconfig, but i have no problem accessing the network and surfing the internet. 
this error is quite annoying, since my NIC doesn't seem to respond at it's "usual" address of 192.168.0.* and i can't access my PC over LAN.

btw, my network card is an integrated nvidia chip (nforce2), which used to work flawlessly in breezy and even ubuntu 6.06, so i don't think it's driver-related.

---

### Post by aay on 2006-09-26
I found this thread after finding out that two of the computers on my lan had changed their ip addresses from 192.168.*.* to 169.254.*.*  I was freaking out at first, but now it seems that this change is do to the fact that I installed zeroconf on both of these boxes.  Actually it appears that both computers are still reachable through their 192.168 addresses, but if I do an ifconfig they both show up as 169.254.*.*  Anyway I just wanted to let others know who are having this problem, that it's really not a problem at all and that it's probably only happening because you have installed zeroconf.

---

### Post by woody7 on 2006-10-04
kzutter's interfce file worked for me when I had to set my Ubuntu Server to a fixed IP.

I had made the changes from another example, did /etc/init.d/networking restart, but ifconfig did not see the eth0 NIC at all.

I added kzutter's suggestion of "auto eth0" to the end of my interface file, re-did the restart command above, and ifconfig now shows the eth0 NIC, with it's correctly associated fixed IP address.

Maybe adding "auto eth0" to your interfaces file will work.

... Woody

---

