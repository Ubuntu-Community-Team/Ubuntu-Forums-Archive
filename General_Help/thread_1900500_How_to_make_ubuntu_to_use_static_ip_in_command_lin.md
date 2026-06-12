---
title: "How to make ubuntu to use static ip in command line ?"
date: 2011-12-26
forum: General Help
---

### Post by ningji on 2011-12-26
The latest ubuntu is using network-manager to set static/dhcp.
So i cannot use command line to change this anymore ?


BTW,
in /etc/network/interfaces,
i only see 
auto lo
iface lo inet loopback

nothing configured for eth0.

But when i boot up, it's using dhcp ?
Where does it get the configuration now ?

Believe I'm using ubuntu 11.04.

---

### Post by zvacet on 2011-12-26
Read [this]("http://ubuntuforums.org/archive/index.php/t-1869754.html"),maybe you will find it helpful.

---

### Post by ningji on 2011-12-27
> **zvacet said:**
> Read [this]("http://ubuntuforums.org/archive/index.php/t-1869754.html"),maybe you will find it helpful.

didn't see a good solution,
thanks anyway !

---

### Post by Lars Noodén on 2011-12-27
You could do something like this in [font=Courier New]/etc/network/interfaces[/font]

```

iface eth0 inet static
   address 192.168.1.25
   broadcast 192.168.1.255
   netmask 255.255.255.255
   gateway 192.168.1.1

```

Look at the manual page for [interfaces](http://manpages.ubuntu.com/manpages/oneiric/en/man5/interfaces.5.html) for the technical details.

---

### Post by vangop on 2011-12-27
If I understood the question...
Ubuntu uses NM, so all the interfaces NOT listed in /etc/network/interfaces are managed by NM. This is how eth0 gets its address.
If you want a static IP you can set it in NM, or if you want command line you can ```
ifconfig eth0 xxxx.xxxx.xxxx.xxxx
```
Also you can use the static config in /etc/network/interfaces

---

### Post by tkoco on 2011-12-27
> **ningji said:**
> The latest ubuntu is using network-manager to set static/dhcp.
So i cannot use command line to change this anymore ?


SNIP

Try this solution:

[http://ubuntuforums.org/showthread.php?t=1259634]("http://ubuntuforums.org/showthread.php?t=1259634")

---

### Post by ningji on 2011-12-27
> **tkoco said:**
> Try this solution:

[http://ubuntuforums.org/showthread.php?t=1259634]("http://ubuntuforums.org/showthread.php?t=1259634")

Thanks very much, will give it a try.

---

