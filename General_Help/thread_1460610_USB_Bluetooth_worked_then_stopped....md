---
title: "USB Bluetooth worked then stopped..."
date: 2010-04-23
forum: General Help
---

### Post by aljones15 on 2010-04-23
Plugged in a new usb blue tooth device and ubuntu immediately recognized it, and it worked. now it doesn't work. It doesn't matter if I turn blue tooth off or on the icon remains slightly faded in the tool bar and it doesn't allow me to connect to blue tooth devices..
when I open preferences it says bluetooth is disabled.

 Here is the hciconfig

hciconfig -a
hci0:	Type: USB
	BD Address: 00:1F:81:00:02:50 ACL MTU: 1021:4 SCO MTU: 180:1
	UP RUNNING 
	RX bytes:59 acl:0 sco:0 events:5 errors:0
	TX bytes:15 acl:0 sco:0 commands:6 errors:1
	Features: 0xff 0x3e 0x0d 0x76 0x80 0x01 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 
	Name: 'Accel-OB2'
Can't read class of device on hci0: Connection timed out (110)

Anyone?

Thanks,
Andrew

turns out

sudo /etc/init.d/bluetooth start

gets it working. anyway to make it do that automatically when the device is plugged in?

---

### Post by CannibalZerg on 2010-04-23
I has the same problem with my BlueTooth USB dongle few month ago on my laptop. It has stopped working after couple "hciconfig -a" commands with error #110 (but it was working fine in Windows). I've been tried various Live-CD distros (64bit/32bit, with various kernel versions, with various bluez versions) with no result.
My solution was to buy another dongle (from another vendor), and I was lucky this time, it's working just fine.
But two weeks ago I've been finished to configure my home server with low-power VIA-C3@600Mhz with Ubuntu Server 9.10 32bit. I remembered about that "buggy" BT dongle and plugged it in to test it again. It was working with no errors. And it's still working fine, but only on my "server". So it seems a hardware-specific  bug in driver.
I think that the best solution is to test the dongle before buying it.

---

### Post by klemes on 2010-04-23
I have a similar issue here and I have found out that unplugging the dongle from the USB port and simply reinserting it does the trick for me.

---

