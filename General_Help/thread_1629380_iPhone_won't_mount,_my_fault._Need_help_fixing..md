---
title: "iPhone won't mount, my fault. Need help fixing."
date: 2010-11-23
forum: General Help
---

### Post by timbalisto on 2010-11-23
I recently installed Maverick after using Intrepid for a while. I like that I can plug in my iPhone and have it auto mount on my desktop, but I didn't like the boxes popping up asking what I wanted to do with this device that has pictures and music on it. So I eventually selected for both of them to do nothing. Now the phone won't mount, it doesn't show up in the devices that I *can* mount either. I plug it in and the phone knows it's plugged in, it even shows up when I do an lsusb in a terminal. 
Here is the syslog when I plug it in:
```
Nov 23 18:07:13 home-GT5408 kernel: [ 4857.252080] usb 1-6: new high speed USB device using ehci_hcd and address 42
Nov 23 18:07:14 home-GT5408 kernel: [ 4857.948801] usb 1-6: new high speed USB device using ehci_hcd and address 43
Nov 23 18:07:14 home-GT5408 kernel: [ 4858.640189] usb 1-6: new high speed USB device using ehci_hcd and address 44
Nov 23 18:07:15 home-GT5408 kernel: [ 4859.208065] usb 1-6: new high speed USB device using ehci_hcd and address 45
Nov 23 18:07:16 home-GT5408 kernel: [ 4859.932262] usb 4-2: new full speed USB device using uhci_hcd and address 9
Nov 23 18:07:16 home-GT5408 kernel: [ 4860.081206] usb 4-2: not running at top speed; connect to a high speed hub
Nov 23 18:07:16 home-GT5408 kernel: [ 4860.546175] ipheth 4-2:4.2: Apple iPhone USB Ethernet device attached
Nov 23 18:07:16 home-GT5408 usbmuxd[3145]: [2] Could not get device list: -1

```
And when I unplug it:
```
Nov 23 18:08:29 home-GT5408 kernel: [ 4933.632237] usb 4-2: USB disconnect, address 9
Nov 23 18:08:29 home-GT5408 kernel: [ 4933.648619] ipheth 4-2:4.2: Apple iPhone USB Ethernet now disconnected
```

I would like to be able to mount it again, any help is appreciated.

---

### Post by nl4m on 2010-11-23
Try copying the mount files from the LiveCD to your HDD, and backing up the old ones.

---

### Post by timbalisto on 2010-11-24
Do you mean creating a mount point for the phone in /media, how would I go about doing that? It seems like I should be able to fix this with the toggle of an option in some settings menu.

---

### Post by timbalisto on 2010-11-24
I fixed it. I changed some options in nautilus preferences and after a reboot it all worked fine again.

---

