---
title: "USB connection attempt to a Galaxy Tab 7 plus"
date: 2012-06-24
forum: General Help
---

### Post by Lugligino on 2012-06-24
I'm trying to connect a Galaxy Tab 7 plus to my PC (lubuntu 12.04). The usb connection works not so perfectly: lubuntu gives  
**[*Error initializing camera*: -60: Could not lock the *device*]("https://www.google.it/url?sa=t&rct=j&q=&esrc=s&source=web&cd=5&ved=0CH8QFjAE&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F331681&ei=uRDnT8inG7L54QS1yPW9AQ&usg=AFQjCNE7CSO4f8FmwmA0Ms4Ww-uZv0G8Iw&sig2=x5Wlg5eeRiT8pv2M5VzWsA&cad=rja")**

and asks if I prefer to open the device (a portable audio player #-o) with vlc or open in file manager. Obviously I open file manager and I can see the sd card directories but they are empty :-k. If I try to copy files, it's not allowed.

dmesg gives: ```
[ 2500.812120] usb 1-3: new high-speed USB device number 5 using ehci_hcd
[ 2500.944503] usb 1-3: config 1 has no interfaces?
[ 2500.948792] cdc_acm 1-3:2.0: This device cannot do calls on its own. It is not a modem.
[ 2500.949102] cdc_acm 1-3:2.0: ttyACM0: USB ACM device
[ 2502.198510] usb 1-3: USB disconnect, device number 5
[ 2502.472068] usb 1-3: new high-speed USB device number 6 using ehci_hcd
[ 2502.604661] usb 1-3: config 1 has no interfaces?
[ 2502.608810] cdc_acm 1-3:2.0: This device cannot do calls on its own. It is not a modem.
[ 2502.609060] cdc_acm 1-3:2.0: ttyACM0: USB ACM device
[ 2513.641544] usb 1-3: USB disconnect, device number 6
[ 2520.708120] usb 1-3: new high-speed USB device number 7 using ehci_hcd
[ 2520.840483] usb 1-3: config 1 has no interfaces?
[ 2520.844526] cdc_acm 1-3:2.0: This device cannot do calls on its own. It is not a modem.
[ 2520.844672] cdc_acm 1-3:2.0: ttyACM0: USB ACM device
[ 2522.086243] usb 1-3: USB disconnect, device number 7
[ 2522.360105] usb 1-3: new high-speed USB device number 8 using ehci_hcd
[ 2522.492615] usb 1-3: config 1 has no interfaces?
[ 2522.496760] cdc_acm 1-3:2.0: This device cannot do calls on its own. It is not a modem.
[ 2522.497009] cdc_acm 1-3:2.0: ttyACM0: USB ACM device
[ 2545.632522] usb 1-3: USB disconnect, device number 8
[ 2545.904096] usb 1-3: new high-speed USB device number 9 using ehci_hcd
[ 2582.408852] usb 1-3: USB disconnect, device number 9
[ 2582.680093] usb 1-3: new high-speed USB device number 10 using ehci_hcd
[ 2588.811656] usb 1-3: USB disconnect, device number 10
[ 2589.084115] usb 1-3: new high-speed USB device number 11 using ehci_hcd
[ 3117.923776] udevd[3345]: starting version 175
[ 3124.369047] usb 1-3: USB disconnect, device number 11
[ 3130.712076] usb 1-3: new high-speed USB device number 12 using ehci_hcd
[ 3132.436168] usb 1-3: USB disconnect, device number 12
[ 3132.708095] usb 1-3: new high-speed USB device number 13 using ehci_hcd

```lsusb  gives: ```
Bus 001 Device 013: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
```I suspected that an udev rule was necessary so I tried with 
```
SUBSYSTEM==&#8221;usb&#8221;, SYSFS{idVendor}==&#8221;0x04e8&#8243;, MODE=&#8221;0666"
```but no result.
Any hints?

---

### Post by Lugligino on 2012-06-25
I found this (inelegant) solution:

[LIST=1]
[*]umount sd card
[*]extract it from the Galaxy tab
[*]insert in a usb card reader
[*]connect to PC
[*]The system mount it on /mnt/sdb1
[*]I can read or write data
[*]umount
[*]extract it from card reader
[*]Insert and mount sd card in the Galaxy Tab
[/LIST]
It works but I would like to use usb cable (too much time wasting).
Any better idea?

---

### Post by Lugligino on 2012-06-26
I followed step 1-12 of this procedure [HTML]http://forum.xda-developers.com/showthread.php?t=1077377[/HTML] and tried this udev rule:
```
ACTION!="add", 
GOTO="gtab_rules_end" 
SUBSYSTEM!="usb|usb_device", GOTO="gtab_usb_end"  
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="6860", MODE="0777" SYMLINK+="gtab"
LABEL="gtab_usb_end"  
LABEL="gtab_rules_end"
```but no changes at all.

---

### Post by Man_Beach on 2012-06-26
If you search in the forums for samsung galaxy tab there are quite a few threads and no-one seems to have a solution, other than to copy files via a micro sd card.

---

### Post by Lugligino on 2012-06-27
> **Man_Beach said:**
> If you search in the forums for samsung galaxy tab there are quite a few threads and no-one seems to have a solution, other than to copy files via a micro sd card.
Yes, it is. Samsung and a lot of other phones manufacturers use Android (that was born from Linux) earning a lot of money and makes this sh:-#tty USB PC-Phone connection usable from Windoze (not exactly a Linux friend) and MAC (derived from linux, also) users only. So Windoze and MAC business increases using open-source efforts. Gratitude seems not to be the Samsung (and others) forte [-X.

---

