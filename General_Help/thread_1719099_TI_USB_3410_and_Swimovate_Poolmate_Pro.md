---
title: "TI USB 3410 and Swimovate Poolmate Pro"
date: 2011-04-01
forum: General Help
---

### Post by KendrickHamilton on 2011-04-01
Hello All,
   I just got a swimovate poolmate pro swimming watch. It includes a download pod for downloading the swimming info to my computer. The pod appears to use a TI3410 USB<->serial converter. I modified the ti_usb_3410_5052 to include poolmate's USB ID numbers. When I connect the pod, I get this error from dmesg:

[ 3618.658950] USB Serial support registered for TI USB 3410 1 port adapter
[ 3618.658964] USB Serial support registered for TI USB 5052 2 port adapter
[ 3618.659353] ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter converter detected
[ 3618.659364] usb 2-2: firmware: requesting ti_usb-v0451-p5051.fw
[ 3618.678673] usb 2-2: firmware: requesting ti_3410.fw
[ 3619.700850] usb 2-2: ti_download_firmware - error downloading firmware, -110
[ 3619.700874] ti_usb_3410_5052: probe of 2-2:2.0 failed with error -5
[ 3619.700907] usbcore: registered new interface driver ti_usb_3410_5052
[ 3619.700910] ti_usb_3410_5052: v0.9:TI USB 3410/5052 Serial Driver
[ 3620.163997] __ratelimit: 6 callbacks suppressed
[ 3620.164000] type=1503 audit(1301664362.336:22):  operation="open" pid=2933 parent=2920 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"

Can anybody help?

I am running ubunt 10.04

---

### Post by ivor on 2012-02-21
Hi sorry for bumping such an old thread, but I just came across  your question.
I have dome some work getting the poolmate running under linux although I didn't manage to get the ti_usb_3410_5052 working with it (yet) I did produce a userspace driver and viewer app: [http://code.google.com/p/poolviewer](http://code.google.com/p/poolviewer) for it that you might find helpful.

---

