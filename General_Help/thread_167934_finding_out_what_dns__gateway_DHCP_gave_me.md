---
title: "finding out what dns / gateway DHCP gave me"
date: 2006-04-29
forum: General Help
---

### Post by n3ldan on 2006-04-29
Hi all
I have my laptop running Ubuntu, getting online wirelessly and getting all the settings via DHCP.  I want to see what those settings are.  If I just do ifconfig, it shows me my DHCP given IP and subnet mask.  Where can I see the gateway and dns settings that it gave me?
Thanks

---

### Post by n3tfury on 2006-04-29
I'm very new to linux, but a non-linux way would be supplying us your brand router.  Then, you can test ping a couple of IP's to find out what your LAN gateway's IP is.

---

### Post by cwaldbieser on 2006-04-29
[QUOTE=n3ldan]Hi all
I have my laptop running Ubuntu, getting online wirelessly and getting all the settings via DHCP.  I want to see what those settings are.  If I just do ifconfig, it shows me my DHCP given IP and subnet mask.  Where can I see the gateway and dns settings that it gave me?
Thanks[/QUOTE]
```

$ route

```
will show you your default route (i.e. the gateway).

DNS settings are in /etc/resolv.conf.

---

### Post by n3tfury on 2006-04-29
or that :P

now I know too.

---

### Post by n3ldan on 2006-04-29
perfect, thanks

---

