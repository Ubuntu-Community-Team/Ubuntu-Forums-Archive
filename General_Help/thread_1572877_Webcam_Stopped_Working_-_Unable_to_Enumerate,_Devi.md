---
title: "Webcam Stopped Working - Unable to Enumerate, Device not accepting address"
date: 2010-09-11
forum: General Help
---

### Post by Rabidmonkey1 on 2010-09-11
Hi all, 

I'm hoping someone can help me with my newest webcam issue. My webcam was working perfectly in Lucid until a few days ago, when the video suddenly froze. Naturally I closed stopped the chat, unplugged and reset the device, yet now it was no longer recognized. 

Digging into the logs, it looks like uhci is having trouble assigning the webcam and address. I tried to restart, upgraded to Meerkat Beta to see if the problem would go away, but it hasn't. 

Here're some logs:


Syslog:
```

usb 6-1: new full speed USB device using uhci_hcd and address 6
usb 6-1: device descriptor read/64, error -71
usb 6-1: device descriptor read/64, error -71
usb 6-1: new full speed USB device using uhci_hcd and address 7
usb 6-1: device descriptor read/64, error -71
usb 6-1: device descriptor read/64, error -71
usb 6-1: new full speed USB device using uhci_hcd and address 8
usb 6-1: device not accepting address 8, error -71
usb 6-1: new full speed USB device using uhci_hcd and address 9
usb 6-1: device not accepting address 9, error -71
hub 6-0:1.0: unable to enumerate USB device on port 1

```

Message Log:

```

usb 6-1: new full speed USB device using uhci_hcd and address 6
usb 6-1: new full speed USB device using uhci_hcd and address 7
usb 6-1: new full speed USB device using uhci_hcd and address 8
usb 6-1: new full speed USB device using uhci_hcd and address 9

```

Kern Log:

```

usb 6-1: new full speed USB device using uhci_hcd and address 8
usb 6-1: device not accepting address 8, error -71
usb 6-1: new full speed USB device using uhci_hcd and address 9
usb 6-1: device not accepting address 9, error -71
hub 6-0:1.0: unable to enumerate USB device on port 1

```

So, I think that should give you an idea about what I'm dealing with here. I', usually pretty good with this stuff, but I honestly have no idea how to fix this issue. Thus, any help would be greatly appreciated.

Other info - the Webcam is fairly new. No issues with it on the Windows partition. The USB hub is good too - all my external drives work and my usb mouse works. I really think this is a uhci problem...

Thanks for your help!:KS

---

### Post by dortmann on 2010-09-14
I just encountered this USB error on 10.04.  Simultaneously, my X would not boot.  I noticed "vga16fb" had somehow snuck into the system ... it was missing from etc modprobe.d framebuffer blacklist.

I after adding vga16fb to the blacklist file I have both X and usb functionality again.

DISABLE ALL FRAMEBUFFER MODULES.

lsmod | grep fb


Hope this helps.
[email]dortmann31415@yahoo.com[/email]

---

### Post by tormod on 2010-09-15
> **Rabidmonkey1 said:**
> Hi all, 

I'm hoping someone can help me with my newest webcam issue. My webcam was working perfectly in Lucid until a few days ago, when the video suddenly froze. 
Did this happen after a kernel update? In that case, try installing/running the older kernel.

---

