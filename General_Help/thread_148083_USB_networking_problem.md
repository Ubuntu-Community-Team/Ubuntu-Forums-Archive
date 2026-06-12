---
title: "USB networking problem"
date: 2006-03-21
forum: General Help
---

### Post by Foxmike on 2006-03-21
Hi everybody!

I have a problem about networking.  I'm a newbee in Linux, and I don't know much thing about networking.  I have a Pocket PC with Familiar Linux installed on it.  I want to plug it to my Breezy box and make a USB network for them to speak to each other.  I've followed those HowTos:

> Ubuntu Breezy (5.10) -- Desktop side
Add usbnet to be autoloaded on startup: 

echo "usbnet" > /etc/modutils/usbnet
update-modules 

Add the following to /etc/network/interfaces 

 mapping hotplug       
  script grep       
  map usb0

 iface usb0 inet static
  address 192.168.0.200      
  netmask 255.255.255.0      
  broadcast 192.168.0.255
  pre-up /etc/network/ipaq

Add script /etc/network/ipaq 

 #!/bin/sh
 sleep 5
 exit 0

Ensure that /etc/network/ipaq is executable 

chmod a+x /etc/network/ipaq


and this one from the Familiar Release Notes version v0.8.0 (actually I have v0.8.2 installed)

> If you wish to use USB networking, make the following changes on the iPAQ: 

Edit /etc/hotplug/net.agent 

Change line 29 that reads 

add|register)
to add|register|attach)

Add the following before line 125: 

detach)
    exec /sbin/ifdown $INTERFACE
    ;;

In file /etc/network/interfaces: 

replace line  iface usbf inet dhcp  with this: 

iface usbf inet static
        address 192.168.0.202
        netmask 255.255.255.0
        network 192.168.0.0
        gateway 192.168.0.200


Now, when put the iPaq on the craddle, if I do

> ifconfig

I see usb0 has been activated with IP address:

> 192.168.0.200

When I try to ping the iPaq

> ping 192.168.0.202

then it doesn't work.  Nothing is going through.  But I'm able to ping 192.168.0.200 as well as 192.168.0.100.

I'm pretty shure it's not a big problem but I don't understand a thing about network things... does anyone can help me with this?

Thanks in advance!

-FM

---

### Post by Foxmike on 2006-04-17
Ok well, after all this time I managed to make it work.  Finally understood I had to assing IP addresses to build up a NEW network (192.168.1.XXXinstead of 192.168.0.XXX) because "eht0" was already using network 192.168.0.XXX.

Thanks anyway

-FM

---

