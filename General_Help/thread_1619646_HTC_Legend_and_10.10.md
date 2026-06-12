---
title: "HTC Legend and 10.10"
date: 2010-11-12
forum: General Help
---

### Post by Motherlover on 2010-11-12
Hi there

I have an HTC Legend Android phone and have problems when connecting the device to my laptop. I intend on using the phone as a "disk drive", which is one of the options when I connect my phone to the laptop.

The phone charges and sees itself as being connected, but Ubuntu is not at all aware of the connection - I cannot find the device anywhere. I have tried different USB ports and all of the settings on the phone, but I might've missed something.

Please help!

---

### Post by mcduck on 2010-11-12
This might seem like a obvious question, but have you actually set the phone to act as a disc drive?

If the connection type isn't set to "Disk drive" on the phone, it's not going to do anything else than charge.

Then the troubleshooting part. Open a terminal and run "tail -f /var/log/syslog" and then plug in the phone. You should see some messages appear about how the phone is detected. Post the messages here and hopefully we'll be able to help a bit more. :)

---

### Post by Motherlover on 2010-11-12
Yes, I have set it to be used as a disk drive :)

The results from the troubleshooting:


Nov 12 10:41:32 machiel-Aspire-5920G kernel: [393875.332668] usb 6-2: new full speed USB device using uhci_hcd and address 35
Nov 12 10:41:32 machiel-Aspire-5920G kernel: [393875.752595] usb 6-2: device not accepting address 35, error -71
Nov 12 10:41:32 machiel-Aspire-5920G kernel: [393875.872557] usb 6-2: new full speed USB device using uhci_hcd and address 36
Nov 12 10:41:33 machiel-Aspire-5920G kernel: [393876.292585] usb 6-2: device not accepting address 36, error -71
Nov 12 10:41:33 machiel-Aspire-5920G kernel: [393876.292620] hub 6-0:1.0: unable to enumerate USB device on port 2
Nov 12 10:41:52 machiel-Aspire-5920G kernel: [393895.572598] usb 6-2: new full speed USB device using uhci_hcd and address 37
Nov 12 10:41:52 machiel-Aspire-5920G kernel: [393895.700068] usb 6-2: device descriptor read/64, error -71
Nov 12 10:41:52 machiel-Aspire-5920G kernel: [393895.940197] usb 6-2: device descriptor read/64, error -71
Nov 12 10:41:53 machiel-Aspire-5920G kernel: [393896.172681] usb 6-2: new full speed USB device using uhci_hcd and address 38
Nov 12 10:41:53 machiel-Aspire-5920G kernel: [393896.300083] usb 6-2: device descriptor read/64, error -71
Nov 12 10:41:53 machiel-Aspire-5920G kernel: [393896.542600] usb 6-2: device descriptor read/64, error -71
Nov 12 10:41:53 machiel-Aspire-5920G kernel: [393896.770178] usb 6-2: new full speed USB device using uhci_hcd and address 39
Nov 12 10:41:54 machiel-Aspire-5920G kernel: [393897.190173] usb 6-2: device not accepting address 39, error -71
Nov 12 10:41:54 machiel-Aspire-5920G kernel: [393897.310418] usb 6-2: new full speed USB device using uhci_hcd and address 40
Nov 12 10:41:54 machiel-Aspire-5920G kernel: [393897.730075] usb 6-2: device not accepting address 40, error -71
Nov 12 10:41:54 machiel-Aspire-5920G kernel: [393897.730111] hub 6-0:1.0: unable to enumerate USB device on port 2


Thanks for the help

---

### Post by mcduck on 2010-11-12
oh, that looks pretty bad indeed. The phone and your computer aren't really communicating at all...

Are you using the cable that came with your phone, connected directly to the computer (without any hubs or extension cables)?

Can you try if the connection works on another Linux computer, or perhaps if you boot a live Linux CD? Perhaps try the latest development version of Ubuntu to check that it's not some kernel bug that's already been fixed in new versions?

If nothing else works, you might want to file a bug report about that.

---

### Post by tobey on 2011-04-04
I second this problem. Can anyone point out where and how this bug should be filed.
I don't know if it has been filed already. And if it has been filed already, does it matter to 'second', it to have it solved faster?

---

