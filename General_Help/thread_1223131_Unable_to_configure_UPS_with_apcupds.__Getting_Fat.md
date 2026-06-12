---
title: "Unable to configure UPS with apcupds.  Getting Fatal Error."
date: 2009-07-25
forum: General Help
---

### Post by JockVSJock on 2009-07-25
Greetings, running Ubuntu 8.04 and trying to configure apcupds with a APC 350 ups, which connects to the pc via USB.  I have followed the directions from here: 

[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)


However when running any of the test: 


```
cmmiller@ladytron:/sbin$ sudo ./apctest


2009-07-25 19:10:39 apctest 3.14.2 (15 September 2007) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in device.c at line 70
Unable to create UPS lock file.
  If apcupsd or apctest is already running,
  please stop it and run this program again.
apctest error termination completed

```


```

cmmiller@ladytron:/sbin$ sudo ./apcaccess
FATAL ERROR in apcaccess.c at line 41
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused

```


```

cmmiller@ladytron:/sbin$ lsusb
Bus 003 Device 004: ID 1058:1100 Western Digital Technologies, Inc.
Bus 003 Device 003: ID 045e:0294 Microsoft Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 0000:0000

```


```

cmmiller@ladytron:/etc/default$ cat apcupsd
# Defaults for apcupsd initscript

# Apcupsd-devel internal configuration
APCACCESS=/sbin/apcaccess
ISCONFIGURED=yes

```



I have set the following within /etc/apcupsd

```

UPSNAME APC350
UPSCABLE usb
UPSTYPE usb
NISIP 192.168.1.100

```

Please help...

---

### Post by Midahed on 2009-08-04
I've also been struggling to get apcupsd working.

My situation was a bit different in that if I ran the command lsusb I wasn't even seeing the UPS listed as a usb device.

I have the KDE and Gnome desktops installed under Ubuntu 8.04.3 LTS and read in another thread that Gnome (which I almost never use) has built-in power handling capabilities for a UPS.

I'd originally installed apcupsd, apcupsd-doc and apcupsd-cgi using the Adept package manager, so I uninstalled them again and switched desktop sessions to Gnome.  I then found the UPS was recognised as a usb device and system > preferences > power management now had a tab showing UPS options.

I then switched back to a KDE session and used apt-get to re-install the apcupsd packages.  After that it all worked.

I'm not sure what was going on here.  My settings in /etc/apcupsd/apcupsd.conf and /etc/default/apcupsd were the same as yours throughout my tests, but nothing worked until I'd run it under Gnome and/or uninstalled the original Adept-based installation and re-installed using apt-get.

If you're using Gnome I'd certainly try uninstalling apcupsd and see if the native Gnome power management recognises your UPS.

Hope this might help.  I spend the best part of a day fiddling with mine - now it works and I'm none the wiser why!

Mike

---

