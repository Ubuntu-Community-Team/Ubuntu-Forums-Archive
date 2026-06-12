---
title: "USB Bluetooth adapter not detected at boot - must unplug/plug to be detected {dmesg}"
date: 2011-12-14
forum: General Help
---

### Post by robgill on 2011-12-14
Hi

I have a usb bluetooth adapter (asus bt211) that works in 11.10 if it was plugged in after the system is up. If plugged in before boot or I shut down and turn on with the adapter in, it is not detected. The bluetooth setting says no adapter present. At this point unplug/plug in adapter gives bluetooth access. I include selected dmesg output below. At ~41 I plug in a usb mouse. At ~167 I unplug the bluetooth adapter (recognized as disconnected...) then plug in back in where it is recognized as a bluetooth adapter making my bluetooth keyboard and mouse work.

Any ideas on how to make my system detect the adapter at boot so I don't have to unplug-replug the device everytime? Let me know if I can provide anymore useful info. Thanks for any suggestions.

-rob

```
[   10.166627] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   10.166753] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   10.285431] usb 2-1.7: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
[   10.367617] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   10.430595] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9451 PQ: 0 ANSI: 0
[   10.430623] scsi: killing requests for dead queue
..
..
[   40.890265] usb 3-2: new low speed USB device number 2 using xhci_hcd
[   40.926958] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   40.938934] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   40.943909] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   40.945022] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   41.076489] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   41.113627] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1c.6/0000:06:00.0/usb3/3-2/3-2:1.0/input/input6
[   41.113702] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:06:00.0-2/input0
[   41.113718] usbcore: registered new interface driver usbhid
[   41.113719] usbhid: USB HID core driver
[  167.959356] usb 2-1.7: USB disconnect, device number 3
[  202.361636] usb 2-1.7: new full speed USB device number 5 using ehci_hcd
[  202.690182] usb 2-1.7: USB disconnect, device number 5
[  204.149502] usb 2-1.7: new full speed USB device number 6 using ehci_hcd
[  204.258581] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  204.258788] usbcore: registered new interface driver btusb
[  205.328686] Bluetooth: HIDP (Human Interface Emulation) ver 1.2

```

---

### Post by OneidaLake on 2012-02-21
I realize the original post was from a couple of months ago, but did you ever find a solution?  I also have 11.10 with the same Asus adapter and am experiencing the identical problem.  I installed the adapter back at 11.04 and it worked just fine.  Only when I went to 11.10, did it start exhibiting this behavior. Like you, I unplug/replug and it works just fine.

Not the end of the world, but a bit annoying.

---

### Post by robgill on 2012-02-22
> **OneidaLake said:**
> I realize the original post was from a couple of months ago, but did you ever find a solution?  I also have 11.10 with the same Asus adapter and am experiencing the identical problem.  I installed the adapter back at 11.04 and it worked just fine.  Only when I went to 11.10, did it start exhibiting this behavior. Like you, I unplug/replug and it works just fine.

Not the end of the world, but a bit annoying.

Unfortunately, I still have the same issue. I just don't shut down very often....

---

### Post by OneidaLake on 2012-03-06
Hey, are you still out there?  I actually was able to fix it (at least for me).

Now, you have to understand, that I'm not an expert by any means and I'm kind-of a newcomer to Ubuntu, so please don't rely on my expertise (because I have none).  If you decide to go this route, its at your own risk.

Here's what I did...

It was starting to drive me crazy unplugging/replugging the Bluetooth Dongle and when I googled the issue regarding the Asus dongle, the only pertinent information I found was this thread that you started.

So I decided to find out how Ubuntu recognized the Bluetooth adapter.  At terminal, I typed "lsusb", which showed that it was recognized as "0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth"  Then I googled linux issues with the Atheros AR3011 (using various keywords) and found this set of posts.

[http://www.serverphorums.com/read.php?12,424244](http://www.serverphorums.com/read.php?12,424244)

I think that guy's problem was worse, because it sounded like he had the Atheros built-in, whereas, you and I had the luxury of unplugging/replugging to get ours to work.  So I don't think his was working at all.

Way down at the bottom of the page, he had an "ahaa" moment and discussed a package called "libmtp-runtime". He said that after removing this package, his bluetooth started working.

So what I did was open the Ubuntu Software Center on my laptop and searched for "libmtp-runtime". My system showed that the package was installed.  When I looked at the "More Info", it mentioned something to do with supporting the transfer of music & movies on USB audio & media players.

I removed the "libmtp-runtime" & re-booted.  My Bluetooth icon immediately appeared in the panel and Bluetooth seems to be working without a replug.  I did have to remove my configured Bluetooth devices (speakers, headphones) and re-discover them, but they seem to work just fine.  I re-booted a couple of times and so far have not found any other issues.

Also, after I re-booted a couple of times, I did an apt-get update and apt-get upgrade and noticed the "libmtp-runtime" package didn't come back.  I'm not exactly sure what the package does.

Do you have any thoughts on this and what "ill" effects removing this package may have on my system?

---

### Post by robgill on 2012-03-09
> **OneidaLake said:**
> Hey, are you still out there?  I actually was able to fix it (at least for me).

Now, you have to understand, that I'm not an expert by any means and I'm kind-of a newcomer to Ubuntu, so please don't rely on my expertise (because I have none).  If you decide to go this route, its at your own risk.

Here's what I did...

It was starting to drive me crazy unplugging/replugging the Bluetooth Dongle and when I googled the issue regarding the Asus dongle, the only pertinent information I found was this thread that you started.

So I decided to find out how Ubuntu recognized the Bluetooth adapter.  At terminal, I typed "lsusb", which showed that it was recognized as "0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth"  Then I googled linux issues with the Atheros AR3011 (using various keywords) and found this set of posts.

[http://www.serverphorums.com/read.php?12,424244](http://www.serverphorums.com/read.php?12,424244)

I think that guy's problem was worse, because it sounded like he had the Atheros built-in, whereas, you and I had the luxury of unplugging/replugging to get ours to work.  So I don't think his was working at all.

Way down at the bottom of the page, he had an "ahaa" moment and discussed a package called "libmtp-runtime". He said that after removing this package, his bluetooth started working.

So what I did was open the Ubuntu Software Center on my laptop and searched for "libmtp-runtime". My system showed that the package was installed.  When I looked at the "More Info", it mentioned something to do with supporting the transfer of music & movies on USB audio & media players.

I removed the "libmtp-runtime" & re-booted.  My USB icon immediately appeared in the panel and Bluetooth seems to be working without a replug.  I did have to remove my configured Bluetooth devices (speakers, headphones) and re-discover them, but they seem to work just fine.  I re-booted a couple of times and so far have not found any other issues.

Also, after I re-booted a couple of times, I did an apt-get update and apt-get upgrade and noticed the "libmtp-runtime" package didn't come back.  I'm not exactly sure what the package does.

Do you have any thoughts on this and what "ill" effects removing this package may have on my system?

Interesting, I'll give this a shot - thanks for the info.

---

### Post by OneidaLake on 2012-03-15
OK, I'd be interested to know how you make out.

---

### Post by robgill on 2012-03-15
> **OneidaLake said:**
> OK, I'd be interested to know how you make out.

It seems to have resolved the issue. I think I've only shutdown once since removing that package, but bluetooth worked at login with having to unplug/replug the adapter! Thanks again for the advice.

No ill-effects as far as I can tell, though I don't transfer to any portable media players.

---

