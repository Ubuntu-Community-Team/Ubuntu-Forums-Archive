---
title: "WPA Supplicant versus Keyring Manager"
date: 2006-06-14
forum: General Help
---

### Post by cwmaxson on 2006-06-14
I got this whole network manager thing working before, but now I'm totally ](*,) about this whole process.

I am operating on a BCM 43xx driver and my connection is fine using WEP with the default network monitor.  But when I try to switch to a WPA network using Network Manager with wpa supplicant, nothing happens.  Both the WEP and WPA networks show up on Network Manager, but the Clickity Clickity yields nothing.  I think I have the proper daemons running and gui's installed, but alas, one step seems missing.
My Card supports WPA, and I even had this working a week ago.

PLEASE HELP!

Corey

---

### Post by joshrobinson on 2006-06-14
[QUOTE=cwmaxson]I got this whole network manager thing working before, but now I'm totally ](*,) about this whole process.

I am operating on a BCM 43xx driver and my connection is fine using WEP with the default network monitor.  But when I try to switch to a WPA network using Network Manager with wpa supplicant, nothing happens.  Both the WEP and WPA networks show up on Network Manager, but the Clickity Clickity yields nothing.  I think I have the proper daemons running and gui's installed, but alas, one step seems missing.
My Card supports WPA, and I even had this working a week ago.

PLEASE HELP!

Corey[/QUOTE]


so im guessing you are using the native bcm43xx driver? not an ndiswrapper wrapped version of the windows driver?

i use ndiswrapper, and wpa_supplicant to use that card on my wpa network, you have to manually edit and add some startup scripts, but once going it works fine every time i boot

this is the script i use at boot to startup my network connection
```
lspci -v |grep -i bcm
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper


ifconfig eth0 up
iwconfig eth0 essid "home"
wpa_supplicant -B -D wext -i eth0 -c /etc/wpa_supplicant.conf
sleep 2
dhclient eth0

``` note that i disable bcm43xx(native driver) at boot, remove ndiswrapper module, then load it back in.. then ifconfig brings my wireless card up, sets the ssid as home, then loads my wpa supplicant file, then grabs the information for my ip via dhclient(dhcp)

here is my wpa_supplicant file (edited my key of course)

```
network={
ssid="your ssid network name here"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk="yourkeyhere"
}
```

---

