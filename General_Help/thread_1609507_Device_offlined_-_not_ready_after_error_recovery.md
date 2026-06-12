---
title: "Device offlined - not ready after error recovery"
date: 2010-10-30
forum: General Help
---

### Post by IDNick on 2010-10-30
Hello there, i hope that is somebody who can help me with this problem

I have an USB Sony Micro Vault Pro 8GB [usd8g] an it seems that it is not recognized (neither ubuntu or windows, i'm using ubuntu but i've tried in widows just to be sure is not an OS problem) in order to be mounted.

has anybody an ideea of how can i bring this stupid storing device back to life?

> tail -f /var/log/messages```
Oct 30 19:09:29 God kernel: [ 2271.430987] usb 1-6: USB disconnect, address 7
Oct 30 19:09:34 God kernel: [ 2276.092031] usb 1-5: new high speed USB device using ehci_hcd and address 8
Oct 30 19:09:34 God kernel: [ 2276.225886] scsi9 : usb-storage 1-5:1.0
Oct 30 19:09:56 God kernel: [ 2298.192039] usb 1-5: reset high speed USB device using ehci_hcd and address 8
Oct 30 19:10:06 God kernel: [ 2308.436039] usb 1-5: reset high speed USB device using ehci_hcd and address 8
Oct 30 19:10:22 God kernel: [ 2324.684037] usb 1-5: reset high speed USB device using ehci_hcd and address 8
Oct 30 19:10:22 God kernel: [ 2324.932031] usb 1-5: reset high speed USB device using ehci_hcd and address 8
Oct 30 19:10:33 God kernel: [ 2335.176037] usb 1-5: reset high speed USB device using ehci_hcd and address 8
Oct 30 19:10:33 God kernel: [ 2335.308568] scsi 9:0:0:0: Device offlined - not ready after error recovery
```> sudo fdisk -l```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9487    76195840   83  Linux
/dev/sda2            9487        9730     1952769    5  Extended
/dev/sda5            9487        9730     1952768   82  Linux swap / Solaris
```

---

