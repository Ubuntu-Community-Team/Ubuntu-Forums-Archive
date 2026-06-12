---
title: "d-link wua-2340 installation problem"
date: 2009-12-06
forum: General Help
---

### Post by evaristegalois on 2009-12-06
I am trying to install a wireless interface using D-link WUA-2340. There are good instructions for this, e.g.

[https://help.ubuntu.com/community/WifiDocs/Device/D-Link_WUA-2340](https://help.ubuntu.com/community/WifiDocs/Device/D-Link_WUA-2340)

or

[http://ubuntuforums.org/showthread.php?p=2200725](http://ubuntuforums.org/showthread.php?p=2200725)

or

[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)

The idea is to install ndiswrapper first, which I did successfully so that 'ndiswrapper -v' yields

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.31-16-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 

Then you install the driver by running 'sudo ndiswrapper -i ~/Drivers/NetA5AGU.inf' This also appears to work as 'ndiswrapper -l' gives me the following:

neta5agu : driver installed
	device (07D1:3A08) present

The next step is to activate (?) the device by typing 'sudo modprobe ndiswrapper'. There are no complaints, but in all the instructions it says that that's when the wireless card is supposed to start blinking. No such luck in my case.

[http://ubuntuforums.org/showthread.php?t=503305](http://ubuntuforums.org/showthread.php?t=503305)

seems to have a similar problem, but nobody responded to this particular issue. Here is some output that might help. 'lsusb' gives me:

Bus 001 Device 002: ID 07d1:3a08 D-Link System predator Bootloader Download
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

'dmesg | grep ndiswrapper' yields:

[   20.364365] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   21.133558] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeNumberProcessors'
[   21.133663] ndiswrapper (load_sys_files:206): couldn't prepare driver 'neta5agu'
[   21.138273] ndiswrapper (load_wrap_driver:108): couldn't load driver neta5agu; check system log for messages from 'loadndisdriver'
[   21.138343] usbcore: registered new interface driver ndiswrapper

and 'less /var/log/messages | grep loadndisdriver':

Dec  6 09:11:30 gustav loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver neta5agu
Dec  6 09:21:26 gustav loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver neta5agu
Dec  6 10:08:17 gustav loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver neta5agu

If you have any suggestions or help to offer please do so!

Thanks.

---

