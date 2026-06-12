---
title: "Unable to configure ip address - unknown host.!"
date: 2010-08-10
forum: General Help
---

### Post by agostini on 2010-08-10
Hi, I hope someone can help me with this issue which has suddenly occurred on both my Desktop and my Laptop.
When I try to configure an IP address to any interface I get the following error....

uadmin@Ubuntu:~$ ifconfig br0 addr 192.168.10.1/24
addr: Unknown host
ifconfig: `--help' gives usage information.
uadmin@Ubuntu:~$

I get this for ethernet interfaces as well. I do not understand what is different as I was able to configure the ip address only the day before yesterday on the laptop..?????
The Desktop has had this issue for about 3 weeks now.

br0       Link encap:Ethernet  HWaddr 32:70:40:91:06:25  
          inet6 addr: fe80::3070:40ff:fe91:625/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

uadmin@Ubuntu:~$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.001560b0d46d    no        eth0
                            tap0
virbr0        8000.000000000000    yes        
uadmin@Ubuntu:~$

Any assistance appreciated.

Thanks.

---

### Post by akoskm on 2010-08-10
> **agostini said:**
> Hi, I hope someone can help me with this issue which has suddenly occurred on both my Desktop and my Laptop.
When I try to configure an IP address to any interface I get the following error....

uadmin@Ubuntu:~$ ifconfig br0 addr 192.168.10.1/24
addr: Unknown host
ifconfig: `--help' gives usage information.
uadmin@Ubuntu:~$

I get this for ethernet interfaces as well. I do not understand what is different as I was able to configure the ip address only the day before yesterday on the laptop..?????
The Desktop has had this issue for about 3 weeks now.

br0       Link encap:Ethernet  HWaddr 32:70:40:91:06:25  
          inet6 addr: fe80::3070:40ff:fe91:625/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

uadmin@Ubuntu:~$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.001560b0d46d    no        eth0
                            tap0
virbr0        8000.000000000000    yes        
uadmin@Ubuntu:~$

Any assistance appreciated.

Thanks.

As you can see in
```

ifconfig --help

``` the address need to be specified with the option **add**.
```

ifconfig br0 add 192.168.10.1/24

```.

But you can do it without any extra options simple by typing:
```

ifconfig br0 192.168.10.1/24

```.
Hope this help.

---

### Post by agostini on 2010-08-10
What a "numpty"..!!!!

I'm getting totally confused between setting up ip's on Ubuntu, Cisco and on Juniper (Olive).

Plus I should have read the "command line help" details properly.

Thanks for helping me out.

Cheers...

---

