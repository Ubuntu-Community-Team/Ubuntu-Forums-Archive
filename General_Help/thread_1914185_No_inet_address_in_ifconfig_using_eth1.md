---
title: "No inet address in ifconfig using eth1"
date: 2012-01-23
forum: General Help
---

### Post by curtisk1 on 2012-01-23
Hi I am using Ubuntu 10.04 server and for some reason after i run ifconfig i do not have an inet ip address... however i do have an inet6 address but I cannot ping anything, nor does the server show up on my home network on the router. 

The ethernet cable is plugged in, and this was working in another network previously. Now I have since reinstalled 10.04, and changed networks.

My /etc/network/interfaces file for eth1 is as follows:
auto eth1
iface eth1 inet dhcp

I was reading on potentially disabling IPv6 from [FONT=Verdana]the [/FONT][FONT=Verdana]/etc/modprobe.d/aliases file..
But i do not currently have an aliases file in that directory.

What should I try to do to get it connected to the internet.. keep in mind I am fairly new to this.

Thanks for your help
[/FONT]

---

### Post by papibe on 2012-01-23
Could you tell us a little bit more about your network?

It seems that you have 2 ethernet cards? I guess eth0 is connected to the router and eth1 to a subnet?

Could you post the result of the ifconfig command?

Regards.

---

### Post by curtisk1 on 2012-01-23
ifconfig:

```
eth1   Link encap:Ethernet HWaddr 00::50:fc:1b:94:2c
         inet6 addr: fe80::250:fcff:fe1b:942c/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU 1500 METRIC: 1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:51 dropped:0 overruns:0 carrier:102
         collisions:867 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes:15858 (15.8 KB)
         Interrupt:5 Base address:0xe800
```this and lo are the only ones that show up... when i set it up i remember that there was a problem with finding eth0, so it gave me the option of using eth1 instead and that worked...
However when I set it up I was on a different network... then i moved my computer to my current network.. if that is any help.

---

### Post by papibe on 2012-01-23
To start you don't have your loop back. Make sure your /etc/network/interfaces looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

```
Then restart the network:
```
sudo service networking restart
```
Then post again the result of 'ifconfig'. Please use the code tags (#) available when replying, when pasting command results (it is easier to read :-))

Regards.

---

### Post by curtisk1 on 2012-01-23
[FONT=monospace]Sorry, it does show up... I just didnt write it out... I cant just copy and paste it so i thought it wasnt necessary. But here it is:

[/FONT]```

eth1     Link encap:Ethernet HWaddr 00::50:fc:1b:94:2c          
           inet6 addr: fe80::250:fcff:fe1b:942c/64 Scope:Link          
           UP BROADCAST RUNNING MULTICAST MTU 1500 METRIC: 1          
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
           TX packets:0 errors:51 dropped:0 overruns:0 carrier:102          
           collisions:867 txqueuelen:1000         
           RX bytes:0 (0.0 B) TX bytes:15858 (15.8 KB)         
           Interrupt:5 Base address:0xe800

lo       Link encap: Local Loopback
         inet addr:127.0.0.1 Mask: 255:0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
```

---

### Post by papibe on 2012-01-23
Could you post the result of these 2 commands?
```
sudo lshw -C network


ps aux | grep -i dhc
```
Regards.

---

### Post by curtisk1 on 2012-01-23
sudo lshw -C network:

```

 *-network:0 DISABLED
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       logical name: eth0
       version: 83
       serial: 00:30:18:80:79:53
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:e400(size=256) memory:dd102000-dd102fff memory:10000000-1001ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 00
       serial: 00:50:fc:1b:94:2c
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
       resources: irq:5 ioport:e800(size=32)


```andddd

ps aux | grep -i dhc:

```

root       865  0.0  0.2   2236   512 ?        Ss   18:12   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
curtis    1401  0.0  0.3   3320   840 tty1     S+   20:45   0:00 grep --color=auto -i dhc

```

---

### Post by papibe on 2012-01-23
I have the impression that that eth0 it's better supported. Let's try this:

Change eth1 for eth0 in /etc/network/interfaces, then:
```
sudo ifconfig eth1 down

sudo ifconfig eth0 down
sudo ifconfig eth0 up

sudo service networking restart

```
If that doesn't work post the result of these command:
```
lsmod | grep -i sis900
lsmod | grep -i ne2k-pci

```
Then reverse the try by changing back eth1 on interfaces, and then doing:
```
sudo ifconfig eth0 down

sudo ifconfig eth1 down
sudo ifconfig eth1 up

sudo service networking restart

```
And, it would also be interesting to see this at this point:
```
lsmod | grep -i sis900
lsmod | grep -i ne2k-pci

```
Tell us how it goes.
Regards.

---

### Post by curtisk1 on 2012-01-23
I did the first part... 

after i restarted the network (it said services was an unknown command so i did sudo /etc/init.d/networking restart...) I still did not have internet access... eth0 comes up but now there isnt even an inet6 address.

So i ran lsmod | grep -i sis900
and got:
```

sis900    17176    0
mii         4381      1  sis900 

```and then: lsmod | grep -i ne2k-pci
But nothing came up..

So i then changed back to eth1 
executed the commands you said... and my ifconfig seems to be back to where it started..

then i ran lsmod | grep -i sis900... and lsmod | grep -i ne2k-pci and got the same exact results.

---

### Post by papibe on 2012-01-24
Sorry about that, it is 'service' not 'services' (I fixed it).

What happens if you load the module manually?
```
sudo modprobe ne2k-pci
```
Regards.

---

### Post by curtisk1 on 2012-01-24
I typed the command you said: sudo modprobe ne2k-pci
It seemed like it executed... no confirmation text or error text appeared.. it just went to the next line... my ifconfig command was still the same

So i tried lsmod | grep -i ne2k-pci again.. and still nothing comes up.

Then just looked at lsmod... and found a ne2k**_**pci in the list... instead of ne2k-pci...

So then i ran lsmod | grep -i ne2k_pci and got the following:

```
ne2k_pci    6381   0
8390        8385   1 ne2k_pci
```

---

