---
title: "two nics for same website"
date: 2010-10-22
forum: General Help
---

### Post by zeker446 on 2010-10-22
Hello, my computer is running ubuntu 9.04 and i have to nics and two routers with 2 adsl connection, i want to use them both for the same webite, the first one is working fine, but i seem to cant get the second to open the website, i already port fowarded the router, so it can be a router problem. 

I will leave here my nics configuration:

bulgas@bulgas:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static    
address 192.168.5.203
netmask 255.255.255.0
gateway 192.168.5.253

auto eth1
iface eth1 inet static
address 192.168.5.206
netmask 255.255.255.0


This is my nic configuration.

Please help me, i need to solve this fast.

---

### Post by blueridgedog on 2010-10-22
Have you configured your web server to listen on each IP?

---

### Post by zeker446 on 2010-10-25
I think i have listen to *.8', so it will listen to all ips, i think.

---

### Post by SeijiSensei on 2010-10-25
How are you handling DNS resolution for the hostname?  If there's only one A record for [www.example.com](www.example.com), that's all that will be listening.  You can use "round-robin" DNS to randomly select one name or the other per request with zone file entries like:

```

www     IN    A   192.168.1.1
        IN    A   192.168.1.2

```

I'd also create two explicit <VirtualHost> entries with the two different IP addresses, but otherwise common entries for DirectoryRoot, etc.

```

<VirtualHost 192.168.1.1:80>
     stuff
</VirtualHost>
<VirtualHost 192.168.1.2:80>
     same stuff
</VirtualHost>

```

---

