---
title: "Setting up network printer"
date: 2006-01-25
forum: General Help
---

### Post by kwaanens on 2006-01-25
This has probably been covered a billion times already, but I can't seem to get it to work. I've been through all hits on a search for "network printer" on these forums.

I'd like it simple.
I have a HP deskjet 840c connected to my file server by USB.
I can reach the server with Samba.
I'd like to access the printer with my other Ubuntu machine, as well as XP (dual booting)
The server is behind a router with firewall, so I'd like a minimum of passwords and other obstacles to it.
I'd like the printouts to be sent as fast as possible. (I've tried and tried, and 2 times the printouts came when the server was restarted)
I need to be able to set the printer up to using a4 paper, and not "letter" or anything else. (My last try ended in a weird format. Not a4, that's for sure)

Thanks!

- Ketil

---

### Post by soulestream on 2006-01-25
if you already have cups setup so you can print from the server directly, just use IPP. 

Linux and Windows XP support it natively, samba can be a headache, and IPP is faster.

[Howto]("http://www.gentoo.org/doc/en/printing-howto.xml")

Start at *Configuration* and go down from there. Takes about 5 minutes.

The in windows just setup Internet Printing with 

[http://Ipaddressofserver:631/printers/nameofprinter](http://Ipaddressofserver:631/printers/nameofprinter)

plus with cups setup this way you can manage the printer by going to any machine that has access to printer, open a browser and type

[http://Ipaddressofserver:631](http://Ipaddressofserver:631)

that gives you the cups webmin for management

soule

---

### Post by kwaanens on 2006-01-25
Would this also work with dynamic IP?

- Ketil

---

### Post by soulestream on 2006-01-25
if DHCP and hostnames are setup correctly, then yes.

But why would you setup a dynamic IP on a file server?


soule

---

### Post by kwaanens on 2006-01-25
Just had problems with dhcp, that's all.
I'm trying static now, and see how that goes.

- Ketil

---

### Post by kwaanens on 2006-01-25
After setting  /etc/cups/client.conf to:
ServerName dimension

I get this:

```
$ gnome-cups-manager

** (gnome-cups-manager:9627): WARNING **: IPP request failed with status 1280
```

Also tried "ServerName dimension.ketil"

What am I doing wrong?

- Ketil

---

### Post by soulestream on 2006-01-25
im assuming the hostname of the server is dimension. It probably cant resolve the hostname. 

you can check by opening a terminal and

ping dimension.

if it comes back host unknown you are either going to need to put the address in /etc/hosts

###.###.###.### dimension.ketil dimension  <--with the correct IP of course

or 

just put the IP address of the server in, instead of hostname.

or I like using the cups webmin. It is disabled in Ubuntu by default usually, but you can enable it, by

[http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/](http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/)

then just go through the add a printer wizard.

You may also have to add a real root password to the system

soule

---

### Post by kwaanens on 2006-01-26
[QUOTE=soulestream]im assuming the hostname of the server is dimension. It probably cant resolve the hostname. 

you can check by opening a terminal and

ping dimension.[/QUOTE]

I also tried with dimension.ketil. That gave me the same error.

```
$ ping dimension.ketil
PING dimension.ketil (10.0.0.3) 56(84) bytes of data.
64 bytes from dimension.ketil (10.0.0.3): icmp_seq=1 ttl=64 time=5.16 ms
64 bytes from dimension.ketil (10.0.0.3): icmp_seq=2 ttl=64 time=2.06 ms
64 bytes from dimension.ketil (10.0.0.3): icmp_seq=3 ttl=64 time=2.10 ms

--- dimension.ketil ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 2.064/3.112/5.168/1.453 ms
```

- Ketil

---

### Post by fragmented_user on 2007-04-24
> **kwaanens said:**
> I also tried with dimension.ketil. That gave me the same error.

I had a similar bug. When the bug occurred I had a ServerName listed in my /etc/cups/client.conf that was nonexistent/inaccessible . I commented out the SeverName line in the client.conf file and this bug disappeared.

---

