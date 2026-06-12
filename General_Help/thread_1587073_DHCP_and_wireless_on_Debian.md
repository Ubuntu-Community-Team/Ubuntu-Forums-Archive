---
title: "DHCP and wireless on Debian"
date: 2010-10-02
forum: General Help
---

### Post by coffeebug on 2010-10-02
Sorry  but I don't know what values to pick for address, dns-servers, gateway.  
Hope this will apply to Debian Lenny...

How do I know when I need static ip ?

POS-Compaq:/home/evil# sudo /etc/init.d/networking restart
Reconfiguring network interfaces...There is already a pid file /var/run/dhclient.wlan0.pid with pid 3154
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:5e:f3:8e
Sending on   LPF/wlan0/00:90:4b:5e:f3:8e
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:5e:f3:8e
Sending on   LPF/wlan0/00:90:4b:5e:f3:8e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done.

---

### Post by andrewthomas on 2010-10-03
> **coffeebug said:**
> 
How do I know when I need static ip ?


DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
**No DHCPOFFERS received.**
No working leases in persistent database - sleeping.
done.
It seems that you do need a static IP.  You need to set up your gateway to act as a  DHCP server or configure a static IP.

---

