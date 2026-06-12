---
title: "Usb ports aren't working"
date: 2009-09-05
forum: General Help
---

### Post by luigiU on 2009-09-05
Well, hi all, i'm new to linux, but i have managed to solved all my issues searching the internet... but, i have never found out why my USB Wifi stick disconnects randomly!
Ok, info:

-I don't need USB 2.0 ports(i have 1 but i think is a ubuntu bug)
-I have search and found that maybe is the ehci_hcd module, try to disable ehci_hcd to gain a stable connection(but it seems the module is now part of the kernel(?) so, disable it in modprobe didn't work!
-I have Jaunty(9.04)
-The usb dongle is a D-Link DWA-110(the firmware is not an issue i think, is the USB connection)

So, how any help? I have issues with other USB devices. Except the mouse. I have tried switching ports and now i'm using the back ones.

Thanks. =)

---

### Post by coldReactive on 2009-09-06
Did you install via this method: [Click Here](http://translate.google.com/translate?prev=hp&hl=en&js=y&u=http%3A%2F%2Fwww.vivaolinux.com.br%2Fdica%2FInstalando-o-adaptador-DWA110-no-Ubuntu%2F&sl=pt&tl=en&history_state0=)

---

### Post by luigiU on 2009-09-06
> **coldReactive said:**
> Did you install via this method: [Click Here]("http://translate.google.com/translate?prev=hp&hl=en&js=y&u=http%3A%2F%2Fwww.vivaolinux.com.br%2Fdica%2FInstalando-o-adaptador-DWA110-no-Ubuntu%2F&sl=pt&tl=en&history_state0=")
not needed. already worked, but the conection drops because of the usb ports.. look at dmesg:
```

Sep  5 21:12:33 dan-desktop kernel: [   37.867592] rt73usb 1-3:1.0: firmware: requesting rt73.bin
Sep  5 21:12:33 dan-desktop kernel: [   38.046654] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  5 21:12:36 dan-desktop kernel: [   41.143473] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep  5 21:19:25 dan-desktop kernel: [  449.830413] usb 1-3: USB disconnect, address 3
Sep  5 21:19:26 dan-desktop kernel: [  450.252042] usb 1-3: new high speed USB device using ehci_hcd and address 4
Sep  5 21:19:41 dan-desktop kernel: [  465.588056] usb 1-3: new high speed USB device using ehci_hcd and address 5
Sep  5 21:19:56 dan-desktop kernel: [  480.924073] usb 1-3: new high speed USB device using ehci_hcd and address 6
Sep  5 21:20:12 dan-desktop kernel: [  496.280092] usb 1-3: new high speed USB device using ehci_hcd and address 7
Sep  5 21:20:27 dan-desktop kernel: [  511.612071] usb 1-3: new high speed USB device using ehci_hcd and address 8
Sep  5 21:20:42 dan-desktop kernel: [  526.944053] usb 1-3: new high speed USB device using ehci_hcd and address 9
Sep  5 21:20:58 dan-desktop kernel: [  542.276052] usb 1-3: new high speed USB device using ehci_hcd and address 10
Sep  5 21:21:13 dan-desktop kernel: [  557.608048] usb 1-3: new high speed USB device using ehci_hcd and address 11
Sep  5 21:21:28 dan-desktop kernel: [  572.940077] usb 1-3: new high speed USB device using ehci_hcd and address 12
Sep  5 21:21:44 dan-desktop kernel: [  588.272064] usb 1-3: new high speed USB device using ehci_hcd and address 13
Sep  5 21:21:59 dan-desktop kernel: [  603.604067] usb 1-3: new high speed USB device using ehci_hcd and address 14
Sep  5 21:22:14 dan-desktop kernel: [  618.936023] usb 1-3: new high speed USB device using ehci_hcd and address 15
Sep  5 21:22:30 dan-desktop kernel: [  634.268105] usb 1-3: new high speed USB device using ehci_hcd and address 16
Sep  5 21:22:45 dan-desktop kernel: [  649.600037] usb 1-3: new high speed USB device using ehci_hcd and address 17
Sep  5 21:23:00 dan-desktop kernel: [  664.932025] usb 1-3: new high speed USB device using ehci_hcd and address 18
Sep  5 21:23:16 dan-desktop kernel: [  680.264024] usb 1-3: new high speed USB device using ehci_hcd and address 19
Sep  5 21:23:31 dan-desktop kernel: [  695.596036] usb 1-3: new high speed USB device using ehci_hcd and address 20
Sep  5 21:23:46 dan-desktop kernel: [  710.928025] usb 1-3: new high speed USB device using ehci_hcd and address 21
Sep  5 21:24:02 dan-desktop kernel: [  726.268028] usb 1-3: new high speed USB device using ehci_hcd and address 22
Sep  5 21:24:17 dan-desktop kernel: [  741.600154] usb 1-3: new high speed USB device using ehci_hcd and address 23
Sep  5 21:24:32 dan-desktop kernel: [  756.932059] usb 1-3: new high speed USB device using ehci_hcd and address 24
Sep  5 21:24:48 dan-desktop kernel: [  773.084052] usb 1-4: new high speed USB device using ehci_hcd and address 25
Sep  5 21:25:04 dan-desktop kernel: [  788.416021] usb 1-4: new high speed USB device using ehci_hcd and address 26
Sep  5 21:25:19 dan-desktop kernel: [  803.748048] usb 1-3: new high speed USB device using ehci_hcd and address 27
Sep  5 21:25:34 dan-desktop kernel: [  819.080064] usb 1-3: new high speed USB device using ehci_hcd and address 28
Sep  5 21:25:50 dan-desktop kernel: [  834.507009] usb 1-3: new high speed USB device using ehci_hcd and address 29
```

then i reboot the PC, to make use again of the ports.

---

### Post by coldReactive on 2009-09-06
According to Wifi Docs, it does run out of the box, but also needs manual installation: [Click Here](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB) (But don't click the installation instructions link, as it will be in Portuguese.)

---

### Post by luigiU on 2009-09-06
> **coldReactive said:**
> According to Wifi Docs, it does run out of the box, but also needs manual installation: [Click Here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB") (But don't click the installation instructions link, as it will be in Portuguese.)

didn't work, how can i disable ehci_hcd? I know this is the source as many posts in other forums shows that disabling it helps fix the problem entirely.

---

