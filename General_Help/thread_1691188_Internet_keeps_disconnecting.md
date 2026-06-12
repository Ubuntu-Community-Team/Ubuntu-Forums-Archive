---
title: "Internet keeps disconnecting"
date: 2011-02-19
forum: General Help
---

### Post by ~LoKe on 2011-02-19
This is on my computer only.  My wireless and wired connection keeps dropping, but my wired connection to everything else remains intact.  What could be the cause?  Here's dmesg output, please let me know if I can provide anything else:

> ADDRCONF(NETDEV_UP): wlan0: link is not ready
r8169: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready
r8169: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready
wlan0: authenticate with AP 00:18:e7:ed:73:97
wlan0: authenticated
wlan0: associate with AP 00:18:e7:ed:73:97
wlan0: RX AssocResp from 00:18:e7:ed:73:97 (capab=0x431 status=0 aid=3)
wlan0: associated
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
padlock: VIA PadLock not detected.
wlan0: no IPv6 routers present
wlan0: no probe response from AP 00:18:e7:ed:73:97 - disassociating
ADDRCONF(NETDEV_UP): wlan0: link is not ready
r8169: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready
wlan0: deauthenticating by local choice (reason=3)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
r8169: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
wlan0: deauthenticating by local choice (reason=3)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
wlan0: authenticate with AP 00:18:e7:ed:73:97
wlan0: authenticated
wlan0: associate with AP 00:18:e7:ed:73:97
wlan0: RX AssocResp from 00:18:e7:ed:73:97 (capab=0x431 status=0 aid=1)
wlan0: associated
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present


---

### Post by ~LoKe on 2011-02-22
Still having this problem.  I bought an external wireless adapter and blacklisted the internal one, and I'm still having the same problem.

Any help?

---

### Post by blackcobra on 2011-05-28
more info: 
iwconfig: if there is a wlan0 present from boot then this should not be happening; try: iwlist wlan0 scan! and see if your network is present! if so, and your using a tower desktop, (ie, i don't advise to do this for a laptop) 

(might work, might not)
You could try using wpa_supplicant and dhcpcd. Note! if you do it this way, your will have to manually write the wpa_supplicant.conf, which might pose some difficulty! but its all explained here!

[https://wiki.archlinux.org/index.php/WPA_supplicant](https://wiki.archlinux.org/index.php/WPA_supplicant)

then you could write a small program to do this, something like the following:

#include <stdio.h>
main(void)
{
system("iwconfig wlan0 mode ad-hoc");
system("ifconfig wlan0 up");
system("wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf");
system("dhcpcd wlan0");
}

save as, I don't know, connect.c
gcc -o connect connect.c
sudo cp connect /usr/sbin/

then, 
sudo echo connect & >> /etc/rc.local

Might work, might not. But the reason i do it this way is because i don't like gnome-keyring!

Note! to restart the internet you will have to sudo killall dhcpcd
then, sudo dhcpcd wlan0

---

### Post by linuxinstalledfromhdd on 2011-05-28
If you still can't get it running, what make and model of laptop or desktop computer are you installing this on? 

Have you tried using the Ndiswrapper to install the original windows driver for that Wireless Device?

You can always give this a try:

[http://ubuntuguide.net/how-to-install-windows-wireless-network-card-driver-in-ubuntu](http://ubuntuguide.net/how-to-install-windows-wireless-network-card-driver-in-ubuntu)

---

### Post by blackcobra on 2011-05-28
> **linuxinstalledfromhdd said:**
> If you still can't get it running, what make and model of laptop or desktop computer are you installing this on? 

Have you tried using the Ndiswrapper to install the original windows driver for that Wireless Device?

You can always give this a try:

[http://ubuntuguide.net/how-to-install-windows-wireless-network-card-driver-in-ubuntu](http://ubuntuguide.net/how-to-install-windows-wireless-network-card-driver-in-ubuntu)

hey, I don't know if she needs ndiswrapper if iwconfig has a wlan0 present! but yeah if there is a windows driver that she could use ndiswrapper, probably for the better! but i just notice there on the final message of her dmesg wlan0: no IPv6 routers present. This implies that her blacklisting isn't doing its job properly. ie that its trying to use both wireless cards! internal and external, leading me to assume this is a laptop! but yeah, there is an awful lack of information here! loke more info!

---

