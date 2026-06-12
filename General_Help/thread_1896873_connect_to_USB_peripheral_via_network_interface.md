---
title: "connect to USB peripheral via network interface"
date: 2011-12-18
forum: General Help
---

### Post by ceclauson on 2011-12-18
Okay, so I have a USB peripheral that I'm connecting to as a network interface (I think it's CDC class, but I'm new to this).  I can do it on the Windows partition of my machine, and I'm *close* to doing it on the Linux side, but I'm not quite there.  I'm basically wondering if anyone can offer troubleshooting advice.

The instructions for doing this are to plug the device into the machine via USB, configure the resulting network interface to static ip address 192.168.99.100, subnet mask 255.255.255.0, and then ssh into 192.168.99.101 with a given username and password.

In windows, this works smoothly--I go to network interfaces in the control panel, but the static ip address/subnet mask combo in, ssh, and I'm in.

On Linux, I plug the device in and the network interface "usb0" appears in ifconfig.  I then set the ip address with:

```
ifconfig usb0 192.168.99.100 netmask 255.255.255.0
```

The entry in ifconfig is now:

```

usb0      Link encap:Ethernet  HWaddr 96:a7:3c:1d:cd:cb  
          inet addr:192.168.99.100  Bcast:192.168.99.255 Mask:255.255.255.0
          inet6 addr: fe80::94a7:3cff:fe1d:cdcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:72 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I try to ssh in to 192.168.99.101, but I get the message:
```
ssh: connect to host 192.168.99.101 port 22: No route to host
```

route -v gives:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
192.168.99.0    *               255.255.255.0   U     0      0        0 usb0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

I'm pretty new to networking, so I'm not sure what to try.  If anyone can give me any advice on something obvious or not obvious to try, I'd greatly appreciate it.

Thanks in advance.

---

### Post by akmp on 2012-02-15
Hi ceclauson,
 
I am pretty new to USB networking and i need an urgent help.
 
I need to bring up usb0 interface on my ubuntu machine when i connect a nokia phone.
 
using modprobe i added driver cdc_ncm driver. 
 
When i connect the nokia phone what i see is that one interface comes up that is "usbpn0" and not "usb0", and i feel the usb is mounted as a serial interface since i see
/dev/ttyACM0 and /dev/ttyACM1 come up when phone is connected.
 
i see from your post that you are able to get usb0 interface up, could you please help me in bringing usb0 interface up so that i will be able to assign ip manually/automatically to this interface.
 
Thanking you in advance.
 
With regards
akmp.

---

### Post by dcstar on 2012-02-15
> **ceclauson said:**
> 
..........
```

usb0      Link encap:Ethernet  HWaddr 96:a7:3c:1d:cd:cb  
          inet addr:192.168.99.100  Bcast:192.168.99.255 Mask:255.255.255.0
          inet6 addr: fe80::94a7:3cff:fe1d:cdcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          **TX packets:0 errors:72** dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
.........

It is not working.

---

### Post by akmp on 2012-02-16
Hi ceclauson,
 
I think what you meant was the usb0 interface that you see in you ifconfig is not working.
 
My problem is i am not able to get even the usb0 interface shown in the ifconfig -a listing. Could you please guide the steps/modules that are part of the PC(linux) side which helped in getting the usb0 inferface.
 
With thanks and regards
Aji.

---

