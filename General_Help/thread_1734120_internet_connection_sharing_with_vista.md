---
title: "internet connection sharing with vista"
date: 2011-04-19
forum: General Help
---

### Post by k94382 on 2011-04-19
I have two laptops connected to each other with a crossover cable.
One laptop runs vista and has internet connection sharing enabled and the other laptop has a new installation of ubuntu server 10.10.

The LAN network device is configured as 192.168.0.1 and is on subnet 255.255.255.0.
The ubuntu network device is configured as 192.168.0.1, is on subnet 255.255.255.0, and uses gateway 192.168.0.2. Those are the values that I entered in /etc/network/interfaces.

The laptops are able to ping each other but I am not able to connect to the internet on the ubuntu machine. Am I missing something here? I did

```
sudo /etc/init.d/networking restart
```

and also rebooted the ubuntu machine but no luck. I am unable to update apt-get. Please help.

---

### Post by k94382 on 2011-04-19
Ok, so I was able to resolve the issue but now I would like to know why. I changed

```

iface eth0 inet [B]static
[/B]       address 192.168.0.2
       netmask 255.255.255.0
       network 192.168.0.0
       broadcast 192.168.0.255
       gateway 192.168.0.1

```

to

```

iface eth0 inet [B]dhcp
[/B]#       address 192.168.0.2
#       netmask 255.255.255.0
#       network 192.168.0.0
#       broadcast 192.168.0.255
#       gateway 192.168.0.1

```

and ran ifdown and ifup. Suddenly I get internet access. Why? Why did my setup not work for static but work for dhcp?

---

