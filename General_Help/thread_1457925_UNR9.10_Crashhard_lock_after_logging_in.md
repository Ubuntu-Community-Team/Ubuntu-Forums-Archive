---
title: "UNR9.10: Crash/hard lock after logging in"
date: 2010-04-19
forum: General Help
---

### Post by karl_eller on 2010-04-19
The Hardware: A 2 month old Asus EeePC 1008HA. 1.66 Ghz Atom, 1 Gb RAM, GMA945 integrated graphics, 160gb HDD.

The OS: Ubuntu 9.10 Netbook Remix (also tested regular Ubuntu 9.10 and Kubuntu 9.10 LiveUSBs).

The Problem, In short: Ubuntu locks up after 5-30 seconds of logging in. Most of the time the Capslock light starts flashing, indicating a kernel panic. Also happens when booting off a LiveUSB, although using the ACPI=Off option from the LiveCD allows it to run without crashing.

The Problem, Long Version: Up until yesterday afternoon, the netbook had been working fine. I plugged in my 3G USB Modem, and Ubuntu locked up, with the caps lock light flashing, only way to restart was by holding in the power button until the netbook turned off. Unplugged the USB, restarted, plugged it back in again, same thing happened. Didn't use the netbook again for a few hours, but when I next came to use it, the netbook would crash shortly after logging in. I ran MemTest for 8 hours over-night, and it came up with no errors. Figured it might be a corrupted HDD or install, so I reformatted the hard-drive and tried to re-install UNR 9.10, however the LiveUSB will also freeze shortly after the desktop is displayed. Using the ACPI=Off option let me at least boot in and re-install Ubuntu, however it's still crashing after logging in. Fsck comes up clean. If I use the ACPI=off option in GRUB, the netbook will boot, however it'll be very sluggish and will crash as soon as I try to connect to a network (Wireless, wired or USB 3G).

Any ideas or suggestions as to how I can fix this? The clean UNR9.10 install uses the 1.6.31-14 kernel. I've somehow managed to get it sort-of running with a net connection and a terminal at the moment, so I'm running an update to see if that will fix anything, but I'm not too hopeful.

If this is a hardware problem, that's fine, since the netbook is still under warranty, but I'd rather exhaust all my software solutions before I send the netbook away.

---

### Post by Bungler on 2010-04-19
Seems to me a pretty severe crash, perhaps hardware failure in wireless/Ethernet. Can you read out SMART data?
Can you determine what service makes it crash while logging in? My guess will be when your wireless or Ethernet gets loaded.

---

### Post by karl_eller on 2010-04-19
Where would I get the SMART data from the HDD?

And no, I'm not sure what service is making it crash. When booting without the "quiet" GRUB option, I don't get any errors, and I'm not sure where any other logs would be stored :P

---

### Post by karl_eller on 2010-04-20
Ok, so as a little bit of an update, Windows 7 installed from a USB fine, and everything works without a hitch (Wired network, wireless, USB 3G dongle, bluetooth, etc), and any disk checks turn up clean. However I can still only boot into Ubuntu when using the acpi=off option, which makes Ubuntu extremely slow and unusable, not to mention connecting to a network causes it to crash.

Anybody have any ideas what might be causing this? Possible fixes? I'm not sure it's hardware after-all, since Win7 is working fine, but Ubuntu refuses to work without the ACPI=off switch. I'm using the latest BIOS version (have been the whole time), so updating that isn't possible.

I'm really stumped here, and while Win7 means the netbook is usable again, I really want to go back to UNR 9.10.

---

