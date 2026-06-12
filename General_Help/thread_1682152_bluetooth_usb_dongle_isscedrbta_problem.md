---
title: "bluetooth usb dongle isscedrbta problem?"
date: 2011-02-05
forum: General Help
---

### Post by sdowney717 on 2011-02-05
I plug the dongle usb in and a bluetooth icon appears on the upper panel
but if i try to discover the device, it never finds anything.

got the isscedrbta from XP

lsusb shows nothing

> scott@scott-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0c10:0000  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000 (SN9C20x + OV9650)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2011-02-05
something funny about the ubuntu documentation
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

says to do this but restart says command not found, even though it is installed
Also, I have 2 bluetooth icons showing on the panel

> Open a terminal window and install the required packages with their dependencies:

sudo apt-get install bluez-utils

Connect your Bluetooth device and restart the Bluetooth services:

sudo /etc/init.d/bluez-utils restart

> scott@scott-desktop:~$ sudo apt-get install bluez-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  gambas2-gb-form gambas2-gb-form-dialog libreoffice-filter-binfilter
  gambas2-runtime gambas2-gb-qt libenet0debian1 gambas2-gb-gtk gambas2-gb-gui
  gambas2-gb-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@scott-desktop:~$ sudo /etc/init.d/bluez-utils restart
sudo: /etc/init.d/bluez-utils: command not found
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2011-02-05
alright now it shows up but giving a notification error
adapter not ready
so how to make it ready?

> scott@scott-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000 (SN9C20x + OV9650)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2011-02-05
also keeps popping up this window

It looks like it just does not work yet.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

I put it in my vm of xp and xp finds and installs it properly.

---

### Post by Spyderkid on 2011-02-05
> **sdowney717 said:**
> I plug the dongle usb in and a bluetooth icon appears on the upper panel
but if i try to discover the device, it never finds anything.

got the isscedrbta from XP

lsusb shows nothing

unplug and plug back in your device wait 5 seconds then run [FONT="Courier New"]lsusb[/FONT]

---

### Post by sdowney717 on 2011-02-05
ok, now what?

> scott@scott-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000 (SN9C20x + OV9650)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2011-02-05
it is still busted and unlikely to work

---

