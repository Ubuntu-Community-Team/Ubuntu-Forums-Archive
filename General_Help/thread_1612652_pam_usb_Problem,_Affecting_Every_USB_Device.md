---
title: "pam_usb Problem, Affecting Every USB Device"
date: 2010-11-03
forum: General Help
---

### Post by shoot2kill on 2010-11-03
Hey, i have installed pam_usb for authentication using a USB flash drive instead of manually entering a password, and i followed this official guide here: [http://pamusb.org/doc/quickstart](http://pamusb.org/doc/quickstart)

The guide says that when i unplug the USB drive, the screen should lock, and come back on when i insert it.

what is actually happening, is i am getting logged out every time i plug in or unplug ANY USB device. this has already caused me to lose some work, and i was looking to rectify the problem, and preferably still use pam_usb.

i disabled the gnome-screensaver locking commands in the pamusb.conf but it still keeps doing it, and i suspect it may be something in my common_auth file that is wrong..

below are both of my files, and i appreciate any help. thanks..

pamusb.conf
```

<?xml version="1.0" ?>
<configuration>

	<defaults>
	</defaults>

	<devices>
		<device id="Scala-SmartCard">
			<vendor>Memorex</vendor>
			<model>USB2 ThumbDrive</model>
			<serial>Memorex_USB2_ThumbDrive_2xxxxxxxxxxxx0-0:0</serial>
			<volume_uuid>xxxx-xxxx</volume_uuid>
		</device>
	</devices>

	<users>
		<user id="scalamoosh">
			<device>Scala-SmartCard</device>
		</user>
	</users>
	
	<services>
	</services>

</configuration>

```

common_auth (the relivent lines in order)
```

auth	sufficient			pam_usb.so

auth	[success=1 default=ignore]	pam_unix.so nullok_secure

auth	requisite			pam_deny.so

auth	required			pam_permit.so

auth	optional	pam_ecryptfs.so unwrap

```

lsusb
```

Bus 008 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05a4:2000 Ortek Technology, Inc. WKB-2000 Wireless Keyboard with Touchpad
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB) Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0a16:9005 Trek Technology (S) PTE, Ltd 
Bus 001 Device 003: ID 0d8c:5200 C-Media Electronics, Inc. Mass Storage Controller(0D8C,5200)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jouva on 2010-12-01
If you're still having issues with logging out and X sessions, it's related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451](https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451)

The gdm sessions is crashing due to hal crashing, so it's not so much a "logout" so much as it is a crash.

---

