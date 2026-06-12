---
title: "Internet problem"
date: 2006-06-23
forum: General Help
---

### Post by woopud on 2006-06-23
For some reason my internet doesn't work most of the time, sometimes I reboot and it will work for some time but then quits.  I'm connecting to a actiontec gateway dsl modem, my Windows and PCLinux on the same PC work fine.  I changed the settings in Network Tools from DHCP to Static but no change.  What else can I try ?

Bert

---

### Post by bforbes on 2006-06-24
When it quits, get the output from these commands, and post it here.
```

ifconfig -a
route
cat /etc/network/interfaces

```

---

### Post by woopud on 2006-06-27
woopud@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:29:85:33:CC
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe85:33cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4524975 (4.3 MiB)  TX bytes:173134 (169.0 KiB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

woopud@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         dslmodem.domain 0.0.0.0         UG    0      0        0 eth0
woopud@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
woopud@ubuntu:~$

---

### Post by bforbes on 2006-06-28
Please use code tags in future.

Edit /etc/network/interfaces, remove the line starting with iface eth0 and add this:
```

iface eth0 inet static
    address 192.168.0.3
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

```
You may need to change the gateway address if your router is not 192.168.0.1.

After you've saved that file:
```

sudo ifdown eth0
sudo ifup eth0

```

If that doesn't work, post the output from the same commands as before, and use code tags.

---

### Post by woopud on 2006-06-28
The weird thing is, I had left the PC on all day came home after work and the internet works fine ??

Bert

---

### Post by AirRaven on 2006-06-28
[This](http://www.ubuntuforums.org/showthread.php?t=181171) should solve your problem.

Check Scenestar's tip at the end of the thread. It solved the problem for me.

---

