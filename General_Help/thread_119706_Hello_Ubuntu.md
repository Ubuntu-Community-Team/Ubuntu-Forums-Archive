---
title: "Hello Ubuntu"
date: 2006-01-20
forum: General Help
---

### Post by MKdon on 2006-01-20
Just loaded Ubuntu on my wife's laptop and straight into problems with loading the USB wifi adapter.
Why do the developers mess with the file naming convention surely it's in everyone's interest to keep to the norm.
Loading the driver modules from the readme's depends on the etc directory system to be the same from one release to another let alone one distro to another.
I've loaded the module for a Linksys usb sdapter (rt2570) by hand and lsmod | grep rt2570 shows the following
rt2570         206400   0
usbcore       104188   3   rt2570,uhci_hcd

I would assume from this that it is installed ok!
but ifconfig rausb0 gives an error message No such device!
I've added alias rausb0 rt2570 to /etc/modprobe.d/aliases and to make sure in /etc/modutils I've added a file rt2570 with the same info.
I've edited the interface file to reflect the rausb0 with my Essid etc.
what now any ideas?

---

### Post by nkhansen on 2006-01-20
try running a 

$ tail -f /var/log/messages

while loading the module. Post the output here.

---

### Post by MKdon on 2006-01-20
Sorry its been sometime but I've re-installed Ubuntu and downloaded the rt2570 package again. 
To no avail result is the same.
I get nothing in the /var/messages or syslog only when I unplug the device and replug it it sees a new USB device.
If I look in Device Manager I can see it listed as a Cisco Linksys wlan device.
It works fine on the Suse M/C.
I'll carry on.
Thanks for your interest.

---

