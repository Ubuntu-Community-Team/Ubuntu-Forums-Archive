---
title: "How to install with out a cd drive"
date: 2006-04-27
forum: General Help
---

### Post by jazee on 2006-04-27
Is there a way to install Ubuntu onto a Laptop that the CD Drive has crashed.

My problem is that I have a Dell Inspiron 9100 Laptop that the CD drive died on me and i'm to cheap to buy a new one being I got a new Vaio. Is there a way to install Ubuntu on this system with out using the cd drive. I have tried my only external cd drive i had and it seems to not be detecting the drive or something. I thought about a network install but am having trouble finding information on how to do it.

Anyone have any ideas of how to do it.

---

### Post by tonyr on 2006-04-27
There is apparently a way to do it, but it is not straightforward.  It requires you to
have another machine that is set up as a TFTP or HTTP server.  There does not
seem to be a netboot server for public access out there, at least none
that I have seen mentioned anywhere.  Look at:
[URL="https://wiki.ubuntu.com/Installation/Netboot"]
https://wiki.ubuntu.com/Installation/Netboot[/URL]
for the gory details.  There are a couple of other references that I saw:
[URL="http://gridpt1.fe.up.pt/mlopes/blog/index.php/ubuntu-network-install/"]
http://gridpt1.fe.up.pt/mlopes/blog/index.php/ubuntu-network-install/[/URL]
[URL="http://ubuntuforums.org/showpost.php?p=2493&postcount=2"]
http://ubuntuforums.org/showpost.php?p=2493&postcount=2[/URL]
but these pretty much say the same thing as the wiki document.

---

### Post by jazee on 2006-04-27
In reading those they mention that you need to set up a dhcp server to give an IP address and to point the computer to the install. Is there a way to do this with my netgear router. It already has DHCP running. I just need to figure out how to point it to the file.

---

### Post by tonyr on 2006-04-28
[QUOTE=jazee]In reading those they mention that you need to set up a dhcp server to give an IP address and to point the computer to the install. Is there a way to do this with my netgear router. It already has DHCP running. I just need to figure out how to point it to the file.[/QUOTE]
I don't know, but I don't think so.  I don't know anything about NetGear routers.
The articles assume that the dhcp server and the tftp server are running on the
same machine where the boot and install files are.  Routers like those for home
use generally don't give you that much flexibility (the Linksys WRT54L may be
an exception).

---

