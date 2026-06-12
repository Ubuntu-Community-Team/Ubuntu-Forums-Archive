---
title: "Problems with very slow connection to an external hard drive (it worked fine before)"
date: 2009-09-14
forum: General Help
---

### Post by Seseli on 2009-09-14
I have an iRiver mp3-player which I'm having trouble with. It takes a very long time to move files from the computer to the hard drive on the mp3-player, and sometimes it doesn't work at all. Also, one file on the mp3-player is weird: when I play it, I hear both that file and a deleted file at the same time. A couple of days ago, the mp3-player got disconnected without being unmounted, so the problems could have originated there. 

A while ago, I had other problems with this mp3-player and got good help here. Basically, I was told to run 

tail -n 20 /var/log/syslog

to see if there were errors in the file system, and then run dosfsck. This fixed it. Here's the output of "tail -n 20 /var/log/syslog" now:

Sep 14 20:43:19 tuktoyaktuk kernel: [45556.260038] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:19 tuktoyaktuk kernel: [45556.808033] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:20 tuktoyaktuk kernel: [45558.000063] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:21 tuktoyaktuk kernel: [45558.436067] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:22 tuktoyaktuk kernel: [45559.160036] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:22 tuktoyaktuk kernel: [45559.843615] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:23 tuktoyaktuk kernel: [45560.232546] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:23 tuktoyaktuk kernel: [45560.620053] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Sep 14 20:43:23 tuktoyaktuk kernel: [45560.754168] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 14 20:43:23 tuktoyaktuk kernel: [45560.754176] end_request: I/O error, dev sdg, sector 307848

What does this mean? It looks more like there's a problem with the connection than with the file system? I use the same USB cable and the same USB port on the computer for other devices, which works fine.

---

