---
title: "Changing dhcp client"
date: 2006-03-08
forum: General Help
---

### Post by ljrmorgan on 2006-03-08
Does anyone know how to change dhcp client from dhclient to dhcpcd?

The problem is basically that for some unknown reason dhclient doesn't work for anyone on my uni network, whereas dhcpcd does. I installed dhcpcd from source, and it works when I type "dhcpcd eth0", however I now need dhcpcd to be the default dhcp client, so that I can get an IP address automatically when the computer starts.

I have tried editing /etc/network/interfaces to say

```
iface eth0 inet dhcp
    client dhcpcd
```

However, ifup & whatever networking start-up scripts still calls dhclient (which i cant uninstall as it is a dependency for ubuntu-minimal).

Does anyone have any solutions?

Thanks,

Louis

---

### Post by Pragmatist on 2006-03-08
>  dhclient doesn't work for anyone on my uni network, whereas dhcpcd does.   What does that mean?  dhclient is a dhcp client  and dhcpd is a dhcp server.  The only thing that should have to do with the individual users is the client.

---

### Post by ljrmorgan on 2006-03-08
Yes, but the dhcp **client** dhcpcd works, nothing to do with the **server**, dhcpd.

Basically dhcpcd works and dhclient doesn't, for some unknown reason.

---

### Post by Pragmatist on 2006-03-08
Have you tried the dhcp3 packages such as dhcp3-client and dhcp3-server?

---

### Post by ljrmorgan on 2006-03-08
Just to clarify - I am trying to get an IP address from a server (that I don't have access to) which is running DHCP.

dhclient - which comes with ubuntu - cannot get an IP address, whereas dhcpcd can get one.

Pragmatist: I was under the impression that dhclient was dhcp3-client.

All I need to do is find a file that specifies which dhcp client to use by default, though I don't really know where to look - and I can't find anything about it on the internet.

---

### Post by Pragmatist on 2006-03-08
I would definitely try uninstalling dhclient and installing dhcpcd .  I'm reading around that sometimes they don't play nicely together.  Also, I just read in one of my certification books, that this is actually the recommended method of changing your dhcp client.  On my system I have dhcp3-client and dhcp3-common installed (these are probably the defaults).  Type: **sudo synaptic** to do a search for dhcp and you'll see all of the packages

---

### Post by ljrmorgan on 2006-03-09
[QUOTE=Pragmatist]I would definitely try uninstalling dhclient and installing dhcpcd .  I'm reading around that sometimes they don't play nicely together.  Also, I just read in one of my certification books, that this is actually the recommended method of changing your dhcp client.  On my system I have dhcp3-client and dhcp3-common installed (these are probably the defaults).  Type: **sudo synaptic** to do a search for dhcp and you'll see all of the packages[/QUOTE]

The problem is that when I try to uninstall dhclient it says it's a dependency of ubuntu-minimal - which would presumably leave my system in a bit of a mess :(. I have installed dhcpcd, and it does work when I type "dhcpcd eth0", its just a case of getting it to start by default instead of dhclient - there must be a way.

Thanks for your help,

Louis

---

### Post by Pragmatist on 2006-03-09
> dependency of ubuntu-minimal - which would presumably leave my system in a bit of a mess
According to synaptic, regarding uninstalling ubuntu-minimal:
> It is safe to remove this package if some of the minimal system packages are not desired.   So, I would definitely try my previous suggestion as it won't hurt your system to remove ubuntu-minimal as it is not essential.  If that doesn't help, you could easily reinstall it in synaptic if you wish.

Also, when you do a search using the keyword: **dhcp** tell me all of the packages that are installed (as I mentioned I only have 2--dhcp3-client and dhcp3-common)

---

