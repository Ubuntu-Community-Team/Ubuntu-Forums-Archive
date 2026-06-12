---
title: "USB (driver?) Problems after installing 10.04"
date: 2010-05-24
forum: General Help
---

### Post by User10.04 on 2010-05-24
Hi! I've just installed Ubuntu 10.04 and is experiencing a few problems (extremely old laptop)

 I've got a Medion MIM2080 laptop, 1.5Ghz Celeron M processor and 512 MB  memory.
 
 I have just recently installed Ubuntu 10.04. (Since I do not have an  onboard CD-ROM, the BIOS does not support USB booting and doenst want to  boot from external cd-rom either I did the installation by removing the  hardrive and installing Ubuntu from another computer, which runs Ubuntu  perfectly, btw :))
 
 Now my problem like I said is that my usb transfer rate is extremely  slow. Even if I plug in a mouse it moves erratacally and with a delay.
 
 Following questions asked in the thread "**Re: How do I install USB 2.0  drivers in Ubuntu 9.10?"** I've attached the following info: (i'm new to ubuntu and don't really know what this means and since the problem was never resolved in the other thread i'm still clueless)
 
 Output from ```
sudo lsusb
```:
 ```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 003: ID 1005:b113 Apacer Technology, Inc. Handy Steno  2.0/HT203
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 007: ID 0402:5661 ALi Corp. 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 006: ID 09da:000a A4 Tech Co., Ltd Port Mouse
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
```Bus 001 contains the portable mouse (which only moves with delay  and very erratically, same for 2 other mouse that i tried)
 Bus 002 contains my mp3 player flashdisk (which does not show in  computer but works perfectly on other computer with ubuntu 10.04)
 Bus 003 contains my 2gb flashdisk (which i can browse and copy files  from but is extremely slow)
 
 Output from "sudo dmesg | grep usb" (after some activity such  plugging in and removing usb devices)
 ```
[    0.135448] usbcore: registered new interface driver usbfs
 [    0.135467] usbcore: registered new interface driver hub
 [    0.135501] usbcore: registered new device driver usb
 [    0.258470] usb usb1: configuration #1 chosen from 1 choice
 [    0.259212] usb usb2: configuration #1 chosen from 1 choice
 [    0.260455] usb usb3: configuration #1 chosen from 1 choice
 [    0.261083] usb usb4: configuration #1 chosen from 1 choice
 [  604.324044] usb 1-3: new high speed USB device using ehci_hcd and  address 3
 [  619.880052] usb 1-3: device not accepting address 3, error -110
 [  619.992034] usb 1-3: new high speed USB device using ehci_hcd and  address 4
 [  635.548042] usb 1-3: device not accepting address 4, error -110
 [  635.660034] usb 1-3: new high speed USB device using ehci_hcd and  address 5
 [  646.092049] usb 1-3: device not accepting address 5, error -110
 [  646.204041] usb 1-3: new high speed USB device using ehci_hcd and  address 6
 [  656.636054] usb 1-3: device not accepting address 6, error -110
 [  656.760060] usb 1-4: new high speed USB device using ehci_hcd and  address 7
 [  672.316071] usb 1-4: device not accepting address 7, error -110
 [  672.428082] usb 1-4: new high speed USB device using ehci_hcd and  address 8
 [  687.984045] usb 1-4: device not accepting address 8, error -110
 [  688.096036] usb 1-4: new high speed USB device using ehci_hcd and  address 9
 [  698.528050] usb 1-4: device not accepting address 9, error -110
 [  698.640034] usb 1-4: new high speed USB device using ehci_hcd and  address 10
 [  709.072038] usb 1-4: device not accepting address 10, error -110
 [  709.324042] usb 2-1: new low speed USB device using uhci_hcd and  address 2
 [  712.425064] usb 2-1: configuration #1 chosen from 1 choice
 [  713.266820] usbcore: registered new interface driver hiddev
 [  713.269125] usbcore: registered new interface driver usbhid
 [  713.270629] usbhid: v2.6:USB HID core driver
 [  713.284082] usb 3-1: new full speed USB device using uhci_hcd and  address 2
 [  713.665616] input: A4Tech PS/2+USB Mouse as  /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input8
 [  713.666120] a4tech 0003:09DA:000A.0001: input,hidraw0: USB HID v1.10  Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:10.0-1/input0
 [  714.408058] usb 3-1: not running at top speed; connect to a high  speed hub
 [  716.392290] usb 3-1: configuration #1 chosen from 1 choice
 [  716.686575] usbcore: registered new interface driver usb-storage
 [  716.697319] usb-storage: device found at 2
 [  716.697325] usb-storage: waiting for device to settle before scanning
 [  716.880036] usb 3-2: new full speed USB device using uhci_hcd and  address 3
 [  717.880065] usb 3-2: not running at top speed; connect to a high  speed hub
 [  720.360300] usb 3-2: configuration #1 chosen from 1 choice
 [  720.621484] usb-storage: device found at 3
 [  720.621489] usb-storage: waiting for device to settle before scanning
 [  721.848143] usb-storage: device scan complete
 [  725.818231] usb-storage: device scan complete
 [  819.312093] usb 2-1: USB disconnect, address 2
 [  858.240035] usb 2-1: new low speed USB device using uhci_hcd and  address 3
 [  861.225251] usb 2-1: configuration #1 chosen from 1 choice
 [  862.465394] input: A4Tech PS/2+USB Mouse as  /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input9
 [  862.467852] a4tech 0003:09DA:000A.0002: input,hidraw0: USB HID v1.10  Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:10.0-1/input0
 [ 1004.568082] usb 3-1: USB disconnect, address 2
 [ 1039.220057] usb 1-2: new high speed USB device using ehci_hcd and  address 11
 [ 1054.776046] usb 1-2: device not accepting address 11, error -110
 [ 1054.888058] usb 1-2: new high speed USB device using ehci_hcd and  address 12
 [ 1070.444050] usb 1-2: device not accepting address 12, error -110
 [ 1070.556069] usb 1-2: new high speed USB device using ehci_hcd and  address 13
 [ 1080.988237] usb 1-2: device not accepting address 13, error -110
 [ 1081.100050] usb 1-2: new high speed USB device using ehci_hcd and  address 14
 [ 1091.532052] usb 1-2: device not accepting address 14, error -110
 [ 1091.856087] usb 2-2: new full speed USB device using uhci_hcd and  address 4
 [ 1092.856102] usb 2-2: not running at top speed; connect to a high  speed hub
 [ 1094.840341] usb 2-2: configuration #1 chosen from 1 choice
 [ 1095.102658] usb-storage: device found at 4
 [ 1095.102663] usb-storage: waiting for device to settle before scanning
 [ 1100.296267] usb-storage: device scan complete
 [ 1157.832105] usb 2-1: USB disconnect, address 3
 [ 1161.552113] usb 2-2: USB disconnect, address 4
 [ 1184.472035] usb 1-1: new high speed USB device using ehci_hcd and  address 15
 [ 1200.028040] usb 1-1: device not accepting address 15, error -110
 [ 1200.140070] usb 1-1: new high speed USB device using ehci_hcd and  address 16
 [ 1215.696049] usb 1-1: device not accepting address 16, error -110
 [ 1215.808030] usb 1-1: new high speed USB device using ehci_hcd and  address 17
 [ 1226.240135] usb 1-1: device not accepting address 17, error -110
 [ 1226.352078] usb 1-1: new high speed USB device using ehci_hcd and  address 18
 [ 1236.784061] usb 1-1: device not accepting address 18, error -110
 [ 1237.184083] usb 3-1: new low speed USB device using uhci_hcd and  address 4
 [ 1240.168335] usb 3-1: configuration #1 chosen from 1 choice
 [ 1241.409371] input: A4Tech PS/2+USB Mouse as  /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input10
 [ 1241.412050] a4tech 0003:09DA:000A.0003: input,hidraw0: USB HID v1.10  Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:10.1-1/input0
 [ 1241.668070] usb 2-1: new full speed USB device using uhci_hcd and  address 5
 [ 1242.896114] usb 2-1: not running at top speed; connect to a high  speed hub
 [ 1244.880354] usb 2-1: configuration #1 chosen from 1 choice
 [ 1245.142685] usb-storage: device found at 5
 [ 1245.142690] usb-storage: waiting for device to settle before scanning
 [ 1250.336296] usb-storage: device scan complete
 [ 1571.992151] usb 2-1: USB disconnect, address 5
 [ 1910.512120] usb 3-1: USB disconnect, address 4
 [ 2079.144076] usb 2-2: new low speed USB device using uhci_hcd and  address 6
 [ 2082.128370] usb 2-2: configuration #1 chosen from 1 choice
 [ 2083.369885] input: A4Tech PS/2+USB Mouse as  /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input11
 [ 2083.373701] a4tech 0003:09DA:000A.0004: input,hidraw0: USB HID v1.10  Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:10.0-2/input0
 [ 2112.676072] usb 1-1: new high speed USB device using ehci_hcd and  address 21
 [ 2128.232873] usb 1-1: device not accepting address 21, error -110
 [ 2128.344055] usb 1-1: new high speed USB device using ehci_hcd and  address 22
 [ 2143.900051] usb 1-1: device not accepting address 22, error -110
 [ 2144.012081] usb 1-1: new high speed USB device using ehci_hcd and  address 23
 [ 2154.444087] usb 1-1: device not accepting address 23, error -110
 [ 2154.556075] usb 1-1: new high speed USB device using ehci_hcd and  address 24
 [ 2164.988044] usb 1-1: device not accepting address 24, error -110
 [ 2165.448081] usb 2-1: new full speed USB device using uhci_hcd and  address 7
 [ 2166.448091] usb 2-1: not running at top speed; connect to a high  speed hub
 [ 2168.432379] usb 2-1: configuration #1 chosen from 1 choice
 [ 2168.693733] usb-storage: device found at 7
 [ 2168.693738] usb-storage: waiting for device to settle before scanning
 [ 2173.888702] usb-storage: device scan complete
 [ 4482.768131] usb 2-2: USB disconnect, address 6
 
```It says somewhere that the device is not running at top speed and  that I should plug it into a highspeed hub. Prior to the Ubuntu  installation (I had WinXP Professional) the ports work fine.
 
 Sorry for long message. I'd appreciate anyd help at  least just some pointers. I'm new to Linux/Ubuntu but am a  quick learner :guitar:
 Thank you very much!! (sorry for english)

---

