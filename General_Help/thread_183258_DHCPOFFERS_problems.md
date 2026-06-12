---
title: "DHCPOFFERS problems"
date: 2006-05-27
forum: General Help
---

### Post by terragf on 2006-05-27
recently I've managed to (finally) get ndiswrapper to work with my Dell Inspiron 2200, wireless card: Dell wireless 1370, and driver: bcmwl5.inf

Everything appears to be in running order, except wlan0 cannot detect any signals, and the interface won't enable under kde network settings

When I run sudo dhclient wlan0, it shows:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
, followed by several similar lines with different interval numbers

finally, the last two lines are as follows:
No DHCPoFFERS recieved.
No working leases in persistent database - sleeping.

I also tried using the -s option to enter the ip address at the router, but with no success.


There is a dhcp server running on the router, with over 90 free addresses


Also, I'm not sure if this is related, but when I type iwconfig:
```
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension, but has been compiled with version 17, therefore some driver features may not be available...

wlan0     IEEE 802.11g  ESSID: off/any

```
etc...

The router has an ip address assigned to the computer, but when i tried typing this in manually, nothing changes

any insight would be appreciated, thanks

---

### Post by ash211 on 2006-05-29
I had a similar "No DHCPOffers received" problem as well.  I eventually connected to the internet by using a static ip address.  

How to setup a static ip address:

**GUI way**: 
Click KMenu -> System Settings -> Network Settings
Click "Administrator Mode"
Select your wireless interface and click Configure
Change from automatic (DHCP) to Manual, and enter in the IP address you want your computer to have.  It should be in the 192.168.1.xxx or 192.168.0.xxx range, depending on your router.
OK, and then Apply.

**CLI way**:
```
sudo nano /etc/network/interfaces
```
Change the block with your network interface (ie wlan0) to resemble this:

```

iface wlan0 inet static[INDENT]wireless-essid <your SSID here>
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1[/INDENT]auto wlan0
```

If that doesn't work, it could be that the ndiswrapper isn't properly installed, though I don't have much experience with that area.

---

