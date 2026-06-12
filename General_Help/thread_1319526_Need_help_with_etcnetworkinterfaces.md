---
title: "Need help with /etc/network/interfaces"
date: 2009-11-08
forum: General Help
---

### Post by AndrewRenn on 2009-11-08
Hello there!

I am trying to set up a server for a domain (lets use domain.com as an example.. )

I downloaded Ubuntu 8.04, and I am currently following this tutorial ( [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3) )

I have done part 7 ( Configure The Network ) - then when i try resetting the network ( sudo /etc/init.d/networking restart )
when I have the static stuff set, I get  this error:

SIOCDELRT: No such process

But when I have DHCP set up, I don't get that error.

I'm not necessarily sure if I NEED the static IP, but I know that my IP **does** change sometimes, I've been using no-ip duc on my windows computer, but I dont know if I can get that set up on the server

Here is some information:

I am using VMWare to install this - so I'm not positive on what all IP info I should be using)..

My Subnet mask is 255.255.255.0
The default gateway is 192.168.254.254

Am I filling out the information correctly?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        [B]address 192.168.254.8
        netmask 255.255.255.0
        network 192.168.254.254
        broadcast 192.168.254.254[/B]
       ** gateway 192.168.254.254**

Thanks for all of the help!

/e Now its also saying Failed to bring up eth0

---

### Post by AndrewRenn on 2009-11-08
Bump

---

### Post by jward3010 on 2009-11-08
Broadcast is wrong, it should be: 192.168.254.**255**

---

### Post by falconindy on 2009-11-08
Your network and broadcast are wrong. They should be 192.168.254.0 and 192.168.254.255, respectively. Also, you only need to specify one as they determine the same information.

---

### Post by jward3010 on 2009-11-08
Best way to do this is to edit interfaces and change this info first, then restart networking (like how you did above) and if eth0 is still reported as down type:
```
sudo ifconfig eth0 up
```

---

### Post by jward3010 on 2009-11-08
Best way to do this is to edit interfaces and change this info first, then restart networking (like how you did above) and if eth0 is still reported as down type:
```
sudo ifconfig eth0 up
```

---

### Post by AndrewRenn on 2009-11-08
Alright, tihs is what it looks like now:

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.254.8
    netmask 255.255.255.0
    network 192.168.254.0
    broadcast 192.168.254.255
    gateway 192.168.254.254


when I type /etc/init.d/networking restart I get
*Reconfiguring network interfaces...
*Stopping NTP server ntpd
*Stopping NTP server ntpd
...done.
...done.
[OK]

Then after a few seconds it does

*Starting NTP server ntpd
*starting NTP server ntpd
...done.
...done.

But doesn't say [OK], it just seems to kinda hang there

---

### Post by jward3010 on 2009-11-09
Best way to test network connectivity is use the ping command.

We can do it in three ways, first tests local network connectivity:
```
ping -c 3 192.168.254.254
```
Second tests a connection to the internet:
```
ping -c 3 208.67.222.222
```
Third will test full internet connectivity, with DNS working:
```
ping -c 3 www.google.ie
```

If you get "Destination network unreachable" in any of these then something else is problematic.

---

