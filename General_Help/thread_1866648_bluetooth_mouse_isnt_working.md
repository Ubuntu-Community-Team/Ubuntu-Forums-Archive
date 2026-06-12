---
title: "bluetooth mouse isnt working"
date: 2011-10-21
forum: General Help
---

### Post by ibokozan on 2011-10-21
hello i have a4tech bt-630 bluetooth mouse and 11.10 ubuntu. 



 my mouse is not working properly. 



it should sleep after 5 min. doesnt work.
 

after reboot, does not connect automatically.
 

even paired cursor is not moving but it says connected ! please help.






```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 002: ID 04e8:5f05 Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```

ibokozan@ibokozan-l300:~$ hcitool dev
Devices:
    hci0    00:11:67:CA:A8:2B
```


```

ibokozan@ibokozan-l300:~$ dmesg | tail
[   24.907495] wlan0: RX AssocResp from 00:25:12:be:44:ed (capab=0x411 status=0 aid=1)
[   24.907499] wlan0: associated
[   24.914194] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.878075] input: BlueTooth Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:1/input9
[   33.878221] generic-bluetooth 0005:09DA:80F0.0001: input,hidraw0: BLUETOOTH HID v0.1e Keyboard [BlueTooth Mouse] on 00:11:67:CA:A8:2B
[   35.376019] wlan0: no IPv6 routers present
[   50.452836] input: BlueTooth Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:1/input10
[   50.452981] generic-bluetooth 0005:09DA:80F0.0002: input,hidraw0: BLUETOOTH HID v0.1e Keyboard [BlueTooth Mouse] on 00:11:67:CA:A8:2B
[  117.274468] WARNING! power/level is deprecated; use power/control instead
[  117.352285] usb 2-2: USB disconnect, address 2
```

---

### Post by rllsh57 on 2012-02-18
I have the same problem. My mouse is a4tech BT-630.
```

rush57@rush57-desktop:~$ hcitool dev
Devices:
	hci0	00:11:67:00:00:00
rush57@rush57-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 012: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device

```

---

