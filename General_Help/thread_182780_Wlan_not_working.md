---
title: "Wlan not working"
date: 2006-05-26
forum: General Help
---

### Post by ubuntunewbie on 2006-05-26
I have installed kubuntu (breezy) on my sony vaio.
i have a netgear ma111 usb adapter and am trying to configure my wireless connection to work with kubuntu
i followed exactly all instructions mentioned at this link
[https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111](https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111)

but the wlan is still not working. 

here are some details of what i did

1. /etc/modprobe.conf did not exist with original installation. i created it to add the alias statement

2. i added the following statements at the end of /etc/network/interfaces (abcnet is my essid)

iface wlan0 inet dhcp # if you want dhcp for wireless
auto wlan0 #comment if you don't want it boot at start
     wireless_mode managed
     wireless_essid abcnet
i have disabled encryption for now and so, did not add the encryption related stuff.

When i did sudo ifup wlan0, it says misplaced option and gives line number of the statement - wireless_mode managed

i checked the network interfaces and the system does detect my MA111 wireless usb adapter ( there is an entry out there for it).

Can somebody please help???? I can provide additional details if required.

---

