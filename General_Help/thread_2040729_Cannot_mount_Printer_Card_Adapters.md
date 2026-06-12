---
title: "Cannot mount Printer Card Adapters"
date: 2012-08-11
forum: General Help
---

### Post by Tuxedo Mask on 2012-08-11
I run Precise Pangolin with an HP PSC 1350 (all-in-one) attached. Most everything on the printer works fine; printing is no problem, copying is easy, and scanning works using Ubuntu's built-in scanning programs. The problem comes with the card adapters; specifically, the SD Card scanner, as I don't have media for the other slots to test them out.

When I inserted an SD Card this morning, the light flickered for a bit and the device appeared as "2.0 GB something something" in my list of devices. I mounted it just fine, and was even able to create a folder on it. After a while, however, the folder I was working on disappeared; I opened a new Nautilus browser and found that the card was no longer mounted. When I clicked on the device to mount it again, I was told "/dev/sdd1 is not a valid block file". fdisk -l no longer showed the device; I only had sda, sdb, and sdc, my two harddrives and my phone, respectively. Rebooting did nothing, nor did unplugging the printer from the computer.

One thing to note; after inserting the card again after rebooting and everything, the small "Photo" button lights up. I can press it to create a photo proof sheet, and sure enough the printer is accessing the photo folder on there and showing me the photos I've taken. I cannot seem to find a way to disable this, however.

---

### Post by Tuxedo Mask on 2012-08-23
I don't seem to be able to edit (yet?), so let me add that I tried again after swapping the USB port into which the printer was plugged, and the same things repeated themselves. I can post the relevant dmesg output that roughly corresponds with the events if that would help.

---

### Post by Tuxedo Mask on 2012-10-06
Happened again today. This time I got some messages in dmesg that I didn't get before, so I'll post today's log:

```
[Sat Oct  6 10:07:54 2012] sd 5:0:0:0: >[sdd] 3842048 512-byte logical blocks: (1.96 GB/1.83 GiB)
[Sat Oct  6 10:07:54 2012] sd 5:0:0:0: >[sdd] No Caching mode page present
[Sat Oct  6 10:07:54 2012] sd 5:0:0:0: >[sdd] Assuming drive cache: write through
[Sat Oct  6 10:07:54 2012] sd 5:0:0:0: >[sdd] No Caching mode page present
[Sat Oct  6 10:07:54 2012] sd 5:0:0:0: >[sdd] Assuming drive cache: write through
[Sat Oct  6 10:07:54 2012]  sdd: sdd1
[Sat Oct  6 10:12:01 2012] usblp0: removed
[Sat Oct  6 10:12:01 2012] usb 2-2: >reset full-speed USB device number 2 using uhci_hcd
[Sat Oct  6 10:12:16 2012] usb 2-2: >device descriptor read/64, error -110
[Sat Oct  6 10:12:31 2012] usb 2-2: >device descriptor read/64, error -110
[Sat Oct  6 10:12:31 2012] usb 2-2: >reset full-speed USB device number 2 using uhci_hcd
[Sat Oct  6 10:12:41 2012] usb 2-2: >device descriptor read/64, error -71
[Sat Oct  6 10:12:42 2012] usb 2-2: >device descriptor read/64, error -71
[Sat Oct  6 10:12:42 2012] usb 2-2: >reset full-speed USB device number 2 using uhci_hcd
[Sat Oct  6 10:12:42 2012] usb 2-2: >device not accepting address 2, error -71
[Sat Oct  6 10:12:42 2012] usb 2-2: >reset full-speed USB device number 2 using uhci_hcd
[Sat Oct  6 10:12:43 2012] usb 2-2: >device not accepting address 2, error -71
[Sat Oct  6 10:12:43 2012] usb 2-2: >USB disconnect, device number 2
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >Device offlined - not ready after error recovery
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >[sdd] killing request
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >rejecting I/O to offline device
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >[sdd] Unhandled error code
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >[sdd]  
[Sat Oct  6 10:12:43 2012] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[Sat Oct  6 10:12:43 2012] sd 5:0:0:0: >[sdd] CDB: 
[Sat Oct  6 10:12:43 2012] Write(10): 2a 00 00 03 9b c0 00 00 01 00
[Sat Oct  6 10:12:43 2012] end_request: I/O error, dev sdd, sector 236480
[Sat Oct  6 10:12:43 2012] Buffer I/O error on device sdd1, logical block 236343
[Sat Oct  6 10:12:43 2012] lost page write due to I/O error on sdd1
[Sat Oct  6 10:12:43 2012] usb 2-2: >new full-speed USB device number 3 using uhci_hcd
[Sat Oct  6 10:12:43 2012] usb 2-2: >device descriptor read/64, error -71
[Sat Oct  6 10:12:43 2012] usb 2-2: >device descriptor read/64, error -71
[Sat Oct  6 10:12:43 2012] usb 2-2: >new full-speed USB device number 4 using uhci_hcd
[Sat Oct  6 10:12:43 2012] usb 2-2: >device descriptor read/64, error -71
[Sat Oct  6 10:12:44 2012] usb 2-2: >device descriptor read/64, error -71
[Sat Oct  6 10:12:44 2012] usb 2-2: >new full-speed USB device number 5 using uhci_hcd
[Sat Oct  6 10:12:44 2012] usb 2-2: >device not accepting address 5, error -71
[Sat Oct  6 10:12:44 2012] usb 2-2: >new full-speed USB device number 6 using uhci_hcd
[Sat Oct  6 10:12:45 2012] usb 2-2: >device not accepting address 6, error -71
[Sat Oct  6 10:12:45 2012] hub 2-0:1.0: >unable to enumerate USB device on port 2

```

sdd(1) is apparently the location of the media card reader, but now it cannot be found using fdisk -l nor lsusb.

---

