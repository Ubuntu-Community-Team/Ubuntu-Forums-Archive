---
title: "Artec  Ultima 2000 scanner install problems"
date: 2009-11-25
forum: General Help
---

### Post by Cereus on 2009-11-25
Hello,

I have found some great advice searching the forums but I still can't get my scanner to work.

I have an Artec Ultima 2000 scanner (that's what it says on the back of the scanner anyway)

I found the scanner driver on a backup disk, the file is called gt680xfw.usb (though other posts say the firmware should be called ePlus2k.usb, I can't find that on my backup disk)

lsusb command gives me this output:

> Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385/ScanMagic 1200 UB Plus Scanner
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it appears that it is identified properly (and hmm, Mass Stroage spelling mistake).

I have copied the .usb file to: /usr/share/sane/gt68xx/gt680xfw.usb

Then I sudo gedit /etc/sane.d/gt68xx.conf

and uncommented these lines (and changed path to .usb file)

>  Artec Ultima 2000:
override "artec-ultima-2000" 
firmware "gt680xfw.usb"

However, output from:  scanimage -L

gives:

> WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `gt68xx:libusb:003:004' is a Mustek BearPaw 1200 CU flatbed scanner


And at this point my forum searches haven't given me any further ideas and I would appreciate any pointers.

Thanks

---

