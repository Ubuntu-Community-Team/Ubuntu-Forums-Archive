---
title: "New motherboard and now no network!"
date: 2012-02-02
forum: General Help
---

### Post by zulasmum on 2012-02-02
Hi
I have been running a headless server using Ubuntu 8.04 server edition for storage and printer sharing for 3 years with no trouble.

My motherboard gave up the ghost recently and today I changed it for something similar. The RAM, CPU and HDD are all the same but now I can boot up and log in but there seems to be a problem with eth0. I tried restarting networking but got a load of errror messages such as:

eth0: ERROR while getting interface flags: no such device
Failed to bring up eth0

Not sure what I need to do to resolve this. I'm hoping it isn't going to involve reinstalling the OS.

Thanks
Zulasmum

---

### Post by zulasmum on 2012-02-02
Anyone able to point me in the right direction?

---

### Post by dccombs on 2012-02-02
Disclaimer: I am no Ubuntu Guru by any means!

You changed the MOBO, used the same CPU, but you have the same software?

My guess would be the network chipset is different in your new MOBO, and your OS needs the correct firmware. From what you posted, your system can no longer see eth0.

I don't know nearly enough about Ubuntu, but I'm sure someone will be along soon to tell you how to install the correct firmware.

---

### Post by jonobr on 2012-02-02
Hello

Could you post the results of 
```
/etc/networking/interfaces
ifconfig
dmesg | grep eth
```

also 
```
/etc/resolv.conf
/etc/nsswitch.conf
```

may be of use

thanks

---

### Post by haqking on 2012-02-02
you need to change the ethx entry in

```
/etc/udev/rules.d/70-persistent-net.rules
```

as you have changed your mobo, it is probably now eth1 or such like

cheers

---

### Post by zulasmum on 2012-02-02
Not sure how to copy these files to post them as I have no means of accessing the server at the moment from my other computers, so I shall just type out what I can!

/etc/network/interface shows:

The loopback network interface
auto lo
iface lo  inet loopback

The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.149
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254


ifconfig shows
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inete6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0,0 B)

Will post the other info soon
Thanks

---

### Post by jonobr on 2012-02-02
Your config looks good, but the dmesg may show you have a different eth number as haqking indicated

```
 dmesg |grep eth
```

See if it says eth0 or eth1 or something of that nature.
Im guessing (hoping) it will say something other then eth0

---

### Post by zulasmum on 2012-02-02
dmeg ¦grep eth shows

[ 14.736125] eth0: RTL8169 at 0xf886e000, 00:25:22:ea:a8:8c, XID 281000c0 IRQ 221
[ 18.051294] Driver 'SR' NEEDS UPDATING - PLEASE USE BUS_TYPE METHODS
[ 18.058952] dRIVER 'SD' NEEDS UPDATING - PLEASE USSE BUS_TYPE METHODS
[ 23.879583] UDEV: RENAMED NETWORK INTERFACE ETH0 TO ETH1

---

### Post by jonobr on 2012-02-02
try changing

```
The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.149
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
```

to (see bold)

```
The primary network interface
**auto eth1**
iface eth0 inet static
address 192.168.1.149
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
```

Also- Check the 

```
/etc/udev/rules.d/70-persistent-net.rules
```
as mentioned by haqking that needs to be declared as eth1 also.

Recommend a restart networking when done

```
sudo /etc/init.d/networking restart
```

---

### Post by zulasmum on 2012-02-02
The udev file has 2 lines in it, not sure what to change -

#PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:92:9c:00:d9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

Then another line the same apart from ATTR having different numbers and NAME="eth1"

What do I need to change here please?

---

### Post by jonobr on 2012-02-02
I would reckon you could try one of two things
either comment out the first one in the udev and change the config in /etc/network/interfaces to read eth1

```



#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:92:9c:00:d9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:92:9c:00:d9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```


or leave /etc/network/interfaces the way it is using eth0 and
comment out the second one

```



SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:92:9c:00:d9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:92:9c:00:d9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

I would lean more to trying option 1 and sticking with eth1

---

### Post by zulasmum on 2012-02-02
I've done option 1 and then done the network restart command
I don't think it has helped though!
Should I try option 2?

---

### Post by jonobr on 2012-02-02
Yeah why not , I think you may get the same though.

Last thing to try may be to leave one uncommented and just define eth* instead of one or two

---

