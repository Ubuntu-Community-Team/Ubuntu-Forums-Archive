---
title: "Winfast DTV Dongle Gold"
date: 2009-09-27
forum: General Help
---

### Post by matt-r on 2009-09-27
I´ve basically followed every tutorial known to man on this topic, and now I need professional help.

I have, as the subject suggests, a Winfast DTV Dongle Gold. This has a AF9015 chipset and is a USB DVB-T tuner. I am installing this on Ubuntu 8.10 (Intrepid) on a 60GB PS3 (so PowerPC architecture I think, in my nooby opinion). Obviously, I´m having troubles. Here´s the dmesg output:
```

usb 2-2.1: new high speed USB device using ps3-ehci-driver and address 3
usb 2-2.1: New USB device found, idVendor=0413, idProduct=6029
usb 2-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 2-2.1: Product: WinFast DTV Dongle Gold
usb 2-2.1: Manufacturer: Leadtek
usb 2-2.1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver hiddev
input: Leadtek WinFast DTV Dongle Gold as /class/input/input0
generic-usb 0003:0413:6029.0001: input,hidraw0: USB HID v1.01 Keyboard [Leadtek WinFast DTV Dongle Gold] on usb-sb_05-2.1/input1
usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
```As you can see, it seems to think that the DTV dongle is a human interface device keyboard. I have installed the driver for the chipset (found at [http://linuxtv.org/hg/~anttip/af9015/]("http://linuxtv.org/hg/%7Eanttip/af9015/") ) and I have downloaded dvb-utils, build-essential and mercurial, and ¨make¨d it. Oh. I cant make can I. Nope. No, youve got to go compile the latest kernel. So off I go. Find the latest PS3 kernel. Installed 2.6.31. Then I changed the kernel config (Because the tutorial said to. lol I am such a noob) Then I make make install the kernel. Then I reboot. Then I ran make, make install (Finally!) on the drivers. I also put the firmware from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/") into /lib/firmware (Thats Computer->Filesystem->lib->firmware right?). Then I reboot the PS3. It still doesn´t work. It still thinks its a keyboard. So I tried getting rid of the hid module with ´rmmod usbhid´. In my noobiness, that stuffed my usb keyboards aswell. That made me restart because that is the only keyboard I have that can connect to the ps3 (Ps3s only have USB ports). It seems that I need dvb-usb (What ever that is), because other people who are having troubles getting it to work have dmesg output like:

```
Sep 30 18:33:00 asus kernel:[COLOR=Red] _**dvb-usb**_[/COLOR]: will pass the complete MPEG2 transport stream to the software demuxer.
Sep 30 18:33:00 asus kernel: DVB: registering new adapter (Leadtek WinFast DTV Dongle Gold)
Sep 30 18:33:00 asus kernel:[COLOR=Red] _**dvb-usb**_[/COLOR]: no frontend was attached by 'Leadtek WinFast DTV Dongle Gold'
Sep 30 18:33:00 asus kernel: [COLOR=Red]_**dvb-usb**_[/COLOR]: Leadtek WinFast DTV Dongle Gold successfully initialized and connected.
```(Copied from: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/997883.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/997883.html) )

I then proceeded to download v4l (Maybe it has dvb-usb???). Then I ´make´ then ´make install´ Then I rebooted. Again. It still thinks the dongle is a keyboard. I am running all the commands under root.

Any help to get this to work would be much appreciated. :confused:(Please spell it out for me. I am really nooby)

---

