---
title: "what is the new ubuntu way to turn on ip_forward ?"
date: 2006-06-22
forum: General Help
---

### Post by garyng on 2006-06-22
As title, it seems that ubuntu changes the networking script(used to be debian one) and I don't find a good place to specify this.

anyone knows ?

---

### Post by Stormbringer on 2006-06-23
Take a look into /etc/sysctl.conf ... there you should spot the following lines:

```

# Uncomment the next line to enable packet forwarding for IPv4
#net/ipv4/ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net/ipv6/ip_forward=1

```

Inside of Gnome press ALT+F2, type

   gksudo gedit /etc/sysctl.conf

and uncomment the line you need (IPv4 or IPv6).
Save the change and you're all set.

The enable IP forwarding without rebooting just do a

   sudo echo "1" > /proc/sys/net/ipv4/ip_foward

from within a terminal.

Cheers,
Storm.

---

### Post by garyng on 2006-06-23
[QUOTE=Stormbringer]Take a look into /etc/sysctl.conf ... there you should spot the following lines:

```

# Uncomment the next line to enable packet forwarding for IPv4
#net/ipv4/ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net/ipv6/ip_forward=1

```

Inside of Gnome press ALT+F2, type

   gksudo gedit /etc/sysctl.conf

and uncomment the line you need (IPv4 or IPv6).
Save the change and you're all set.

The enable IP forwarding without rebooting just do a

   sudo echo "1" > /proc/sys/net/ipv4/ip_foward

from within a terminal.

Cheers,
Storm.[/QUOTE]

thanks, I have been trained to the debian way (/etc/network/options) which was also the old ubuntu way. Having looking at it, it seems that sysctl is more natural(and debian used it anyway).

---

### Post by Randomskk on 2006-06-23
I just do this to enable:
```
# echo 1 > /proc/sys/net/ipv4/ip_forward
```

The first mentioned way is probably better, but I guess it's good to know alternatives :P

---

### Post by iperez on 2007-12-23
Doesn't seem to work here. I did the sysctl thing, I rebooted, but unless I manually turn ipforward on with echo in /proc, it doesn't work at all.

It used to work a few days ago, I do update and install new packages so often that I don't really know what package could break it, if any.

---

### Post by david3d on 2008-02-04
In Gusty the default line below in /etc/sysctl.conf doesn't seem to work properly.  Even with the following line uncommented /proc/sys/ipv4/ip_forward will still be 0.
```

net.ipv4.conf.default.forwarding=1

```

The solution to this is to use the following corrected the line in /etc/sysctl.conf.
```

net.ipv4.ip_forward=1

```
--
David

---

### Post by ab_initio on 2008-03-02
Thanks David, this has solved the problem!

---

