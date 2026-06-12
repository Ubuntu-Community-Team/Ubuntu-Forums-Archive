---
title: "dhcp3-server on my computer doesn't respond"
date: 2010-09-11
forum: General Help
---

### Post by ibrabeicker on 2010-09-11
so I need to create a network boot from 1 laptop to another, with a crossover ethernet cable between them, no routers no nothing, my computer is supposed to be the server. I followed half dozen tutorials over the internet but I think my major problem is with the dhcp server

followed this tutorial [http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

but when the client boots it makes several dhcp requests but doesn't respond

wireshark capture looks something like this until the client times out

```
1    0.000000000    0.0.0.0    255.255.255.255    DHCP    DHCP Discover - Transaction ID 0x200d8ad
2    2.253212000    0.0.0.0    255.255.255.255    DHCP    DHCP Discover - Transaction ID 0x300d8ad
3    6.484945000    0.0.0.0    255.255.255.255    DHCP    DHCP Discover - Transaction ID 0x400d8ad
```

My ubuntu is 10.04 32-bits, and I deactivated the wireless connection to do this. Any idea on why my computer doesn't answer the DHCP requests?
[U]

[/U]

---

### Post by CharlesA on 2010-09-11
Do both machines have a gigabit ethernet port? 

Did you already configure dhcp3-server?

---

### Post by ibrabeicker on 2010-09-12
> **CharlesA said:**
> Do both machines have a gigabit ethernet port? 

yes

> **CharlesA said:**
> Did you already configure dhcp3-server?

yes, exactly like this,

[INDENT]```
default-lease-time 600;
max-lease-time 7200;
 option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name “yourdomainname.com”;
 subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.200;
}

```
[/INDENT]As you can see from the wireshark the diskless client is sending DHCP requests but its like my computer doesn't know it is the dhcp server

Also I don't know if it relevant but during my tests my pc didn't had an IP adress. Shouldnt it get an IP from itself?

---

### Post by CharlesA on 2010-09-12
The machine that is the DHCP server needs to have a static IP address, as it will not give one to itself.

Set an ip address in /etc/network/interfaces like so:

```

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Also gigabit ports are Auto MDIX sensing, so they don't need a crossover cable. You can use a regular straight through. :)

---

### Post by ibrabeicker on 2010-09-12
thank you for your response.

The dhcp part worked, but the edit in /etc/network/interface ended up breaking my wlan

a ifconfig shows 

```
eth0      Link encap:Ethernet  Endereço de HW 00:e0:4c:09:68:d8  
          inet end.: 192.168.1.23  Bcast:192.168.1.255  Masc:255.255.255.0[...]

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0[...]

wlan0     Link encap:Ethernet  Endereço de HW 70:f1:a1:5c:46:0d  
          inet end.: 192.168.1.34  Bcast:192.168.1.255  Masc:255.255.255.0[...] 
```

How do I solve this?

And the static IP worked for the DHCP problem, i was wondering if I can have a static IP for eth0 and a different dynamic IP for wlan0?

---

### Post by CharlesA on 2010-09-12
You'd probably have to configure the wireless for static as well.

---

### Post by ibrabeicker on 2010-09-12
ok will try as well

just an update, my dynamic wlan works for a short period of time then after that all the sites timeout

---

### Post by CharlesA on 2010-09-13
Guessing it's losing it's IP or something. The static IP will rule that out.

---

