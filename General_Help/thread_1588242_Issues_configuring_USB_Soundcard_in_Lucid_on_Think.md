---
title: "Issues configuring USB Soundcard in Lucid on Thinkpad W510"
date: 2010-10-04
forum: General Help
---

### Post by utannheim on 2010-10-04
Just got a new Thinkpad W510 at work. It has a combined headphones & mic connector. Unfortunately, I cannot find an adapter for my regular headset with separate headphone & mic jacks. So I have to revert to using a USB Soundcard Adapter that came with the headset. Unfortunately I am running into problems with this too.

Any help greatly appreciated ...

```

~$ tail -f /var/log/messages
Oct  4 21:13:04 one27001 kernel: [  152.347954] usb 3-3: new full speed USB device using xhci_hcd and address 0
Oct  4 21:13:04 one27001 kernel: [  152.380119] xhci_hcd 0000:0f:00.0: WARN: short transfer on control ep
Oct  4 21:13:04 one27001 kernel: [  152.383161] xhci_hcd 0000:0f:00.0: WARN: short transfer on control ep
Oct  4 21:13:04 one27001 kernel: [  152.384250] usb 3-3: configuration #1 chosen from 1 choice
Oct  4 21:13:04 one27001 kernel: [  152.484016] xhci_hcd 0000:0f:00.0: WARN: short transfer on control ep
Oct  4 21:13:04 one27001 kernel: [  152.505431] usbcore: registered new interface driver hiddev
Oct  4 21:13:04 one27001 kernel: [  152.516007] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
Oct  4 21:13:04 one27001 kernel: [  152.517875] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
Oct  4 21:13:04 one27001 kernel: [  152.519870] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
Oct  4 21:13:04 one27001 kernel: [  152.521871] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
Oct  4 21:13:06 one27001 kernel: [  154.520945] usbcore: registered new interface driver snd-usb-audio
Oct  4 21:13:06 one27001 pulseaudio[1878]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1c.6/0000:0f:00.0/usb3/3-3/3-3:1.0/sound/card2 (alsa_card.usb-0d8c_C-Media_USB_Headphone_Set-00-default) more often than 5 times in 10s
Oct  4 21:13:11 one27001 kernel: [  159.514919] generic-usb: probe of 0003:0D8C:000C.0001 failed with error -12
Oct  4 21:13:11 one27001 kernel: [  159.514977] usbcore: registered new interface driver usbhid
Oct  4 21:13:11 one27001 kernel: [  159.514983] usbhid: v2.6:USB HID core driver

```

The outcome, is in Sound Preferences I do not see my adapter. Not sure what other info is useful, but here is output of lsusb:
```

Bus 003 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:480f Lenovo 
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by egrubbs on 2010-10-12
I have two usb audio adapters and neither one of them works with my W510 under 64-bit Lucid or Maverick. Here is one of the bugs I opened: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579040)

On the bright side, I am able to use the combined input/output audio port by using this adapter meant for phones.
[http://www.theheadsetbuddy.com/PC-Computer-Headset-to-35mm-Smartphone-Adapter-01-PC35-PH35.htm](http://www.theheadsetbuddy.com/PC-Computer-Headset-to-35mm-Smartphone-Adapter-01-PC35-PH35.htm)

You can also find it here.
[http://www.amazon.com/gp/product/B002SK66OY/](http://www.amazon.com/gp/product/B002SK66OY/)

---

### Post by jdos2 on 2011-01-21
I'm reviving this oldie for the similar reasons- I simply can't get any of the three USB sound adapters working on my W510, in any of the USB ports.

Devices that can be shown to work on Ubuntu 10.10 32 bit and 64(AMD) on Dell laptops (D600, more modern D630) simply fail with one of several errors on the W510- bandwidth failures, &c.

Trying a more modern kernel (2.6.37-020637rc2-generic) in an effort to get USB working.
Of course this kernel has its own issues- including the ThinkVantage key no longer generating  a keycode, and the USB Bluetooth related errors:
[11523.491763] btusb_bulk_complete: hci0 urb ffff8803e6874f00 failed to resubmit (1)
[11523.491834] btusb_bulk_complete: hci0 urb ffff8803e6874540 failed to resubmit (1)

(and so forth)

What I'm trying to is create an easy connect/disconnect for an Amateur Radio Digital Audio work area. On the Dells, I can bring a laptop in from a hard day at work, plug in to the sound card (and USB serial port adapter that works fine on the W510), turn on the radio, fire up fldigi and flrig, and everything is great. The W510, not so much.

How DOES one go about submitting and troubleshooting USB bugs?

J

---

