---
title: "no wlan after upgrade 10.04 to 12.04 LTS"
date: 2012-08-31
forum: General Help
---

### Post by DrScum on 2012-08-31
Inspiron 6400 intel pro/wireless 3945 working fine on 10.04 LTS, after upgrade to 12.04 LTS no longer working.

Output of dmesg | grep wlan0 is empty
output of rfkill list all shows neither hard nor soft block
dmesg | grep iwl:  shows nothing unusual
lshw -class network shows *network disabled for the wireless interface

iwconfig shows a wireless device wlan0

trying to use ifup wlan0 yields "ignoring unknown device wlan0"

These are the results of about all of the tips I found during a 2h research. Is there anybody able and willing to help me?

---

### Post by DrScum on 2012-09-01
in the mean time I discovered the following:

with the terminal command "sudo service network-manager start"

I can start the network manager, which brings up the wlan adapter. Available networks become visible and I can connect.

However after rebooting I have to go through the same routine again.

By the way: during the boot process the system hangs with the message: "waiting for network configuration" followed by "wating maxiumum of 60s for network configuration" followed by "booting without complete network configuration"

Obviously during the boot process the wlan adapter cannot be started. Does anyone have an idea how to fix this?

---

### Post by claracc on 2012-09-01
I have the same network controller: 10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 

I could never use network manager since lucid lynx, network manager continually connects and desconnects the wifi.

So I ended using wicd, which controls well the wifi.

I recommend to install wicd and then uninstall network manager. The two net managers cannot work together but you nedd any of them in order to download packages.

---

### Post by DrScum on 2012-09-01
followed this thread
[http://ubuntuforums.org/showthread.php?t=1976082](http://ubuntuforums.org/showthread.php?t=1976082)
now the system boots ok and automatically connects to the wireless network.

In short: my wired adapter was set to a static ip on eth0 and eth1, removing that by editing /etc/network/interfaces -essentially commenting out everything related to eth0 and eth1 which leads to the new /etc/network/interfaces content below- fixes the problem

New /etc/network/interfaces:
auto lo
iface lo inet loopback

#iface eth0 inet static
        #address 192.168.0.1
        #netmask 255.255.255.0
        #gateway 192.168.0.1

#auto eth0

        #iface eth1 inet static
        #address 192.168.0.1
        #netmask 255.255.255.0
        #gateway 192.168.0.1

Result: normal boot behaviour (relatively slow though for Ubuntu 12.04 standards)

Although I have the system up and running now, I would be very glad if anyone could tell me what I did and what other problems I might have generated.

---

### Post by DrScum on 2012-09-02
Menawhile tested the behaviour of the LAN adapter:

when connected to a server with IPv4 settings set to Automatic(DHCP) an IP is assigned and the connection works properly (can be pinged from other machines in the network).

With the IPv4 settings set to Manual (fixed IP) the system boots normal and both adapters work fine.


I would really apreciate one of the experts giving me a hint on what happened here, and more importandly on how to avoid it since the upgrade of this one Dell Inspiron was a testrun for a whole computer lab under my supervision. I can't edit the network connection file on each single machine in order to make the wlan work.

---

