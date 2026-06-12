---
title: "Samsung 4828FN - prints but does not detect scanner"
date: 2009-11-14
forum: General Help
---

### Post by Berduchwal on 2009-11-14
I have the following printer Samsung SCX-4828FN.

I installed all three applications supplied by the producer from their website.

Printer works fine with duplex as well.

Scanner sadly is not detected by the Unified Driver Configuration.

I am using 9.10 64bit version.

Previously I had 9.04 32bit and it worked fine.

Version of the driver: 3.00.63

I have reported it to Samsung this morning and waiting for their call back.

For scanning I use Xsane.

Printer is connected by USB.
lsusb
> Bus 002 Device 005: ID 04e8:342d Samsung Electronics Co., Ltd 
reconnection causes:
dmesg
> [ 5955.590408] usb 2-4: new high speed USB device using ehci_hcd and address 6
[ 5955.743053] usb 2-4: configuration #1 chosen from 1 choice
[ 5955.744757] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x04E8 pid 0x342D
[ 5956.940195] usb 2-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1


Any suggestions?

---

### Post by yahs on 2009-11-15
I have posted under HOWTO Install Samsung Unified Printer Driver on the forums. I had similar problems but with a scx4100. Perfect under Hardy and Jaunty but slightly harder under Karmic. My solution was to add myself to the saned group, reboot and everything is perfect again.

---

### Post by Berduchwal on 2009-11-15
Thanks,

I have now read your HOW to and installed version from the repository you created (samsungmfp-driver samsungmfp-data samsungmfp-scanner).

Adding myself to the saned and lp groups did not change anything.

When I run xsane from the terminal I get no device located msg and:

> WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

both when root and as normal user.

Can you suggest anything else I might try?

---

### Post by yahs on 2009-11-15
Sorry I didn't make it clear - The HOWTO belongs to Tweedledee. I have just posted on there. I am using 32 bit so I don't know if 64 bit causes problems. The Unified driver I used was version 3.00.37. In Jaunty I just extracted changed to /cdroot/Linux and ran sudo ./install.sh. Printer and scanner installed without any further problems. In karmic I did exactly the same but like I said I had no scanner until I added myself to saned group

---

### Post by Berduchwal on 2009-11-30
I have spoken with Samsung again today and they said...

that they offer very limited support on Linux as there are nearly no calls to the support centre. He also said that it is the case that Ubuntu community is robust enough to solve problems.

He also said that the HeadOffice have tried to run it on Ubuntu 9.10 successfully but he could not tell me how.

Very interesting approach :)

I have removed packaged and installed from the site following the guide on the website no luck.

---

### Post by ubuntologist on 2009-12-16
not sure if you've seen [http://ubuntuforums.org/showthread.php?p=8508042#post8508042](http://ubuntuforums.org/showthread.php?p=8508042#post8508042) but tobiasly had complete success with the 4826 model. he's also running x64 karmic.

the drivers appear to be the same for both models and i believe the only difference is the duplexing - but i'm new to this...

cheers.

---

### Post by Berduchwal on 2009-12-17
I have had no luck still.

Phoned Samsung again asked them to investigate but no answer still.

---

### Post by Berduchwal on 2010-01-13
Samsung have realised new driver that works for 64bit Ubuntu.

They did it in response to my service request!

This is Linux support how it should be! 

Thanks Samsung!

---

