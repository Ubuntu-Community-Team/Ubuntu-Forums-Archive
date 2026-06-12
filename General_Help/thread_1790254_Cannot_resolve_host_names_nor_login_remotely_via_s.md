---
title: "Cannot resolve host names nor login remotely via ssh"
date: 2011-06-24
forum: General Help
---

### Post by sneakyimp on 2011-06-24
I recently assembled a new computer with both Windows 7 boot and Ubuntu 11.04 boot.  For some reason, I can not resolve domain names at all on in Ubuntu while Windows 7 works just fine.  I'm wondering if I have improperly configured my network settings. I am trying to configure this machine to have a static IP on my network of 192.168.1.3

The machine definitely has its network card installed properly and in Ubuntu I can access numeric ip addresses anywhere via browser or ssh.  When I type in "google.com" in a browser I get an instant 'server not found' error page.

Anything that is described in my hosts file seems to work just fine.  

I can ping my router which has a LAN IP of 192.168.1.1 just fine with no packet loss.

Here are the contents of **/etc/network/interfaces**:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.1.3
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.1

```

If I type in nslookup commands or dig commands they just time out.  Wondering what the story is here.

Also, I am unable to access this machine via ssh from any other machine on the network.  Wondering what might be wrong.  Any tips are greatly desired.

---

