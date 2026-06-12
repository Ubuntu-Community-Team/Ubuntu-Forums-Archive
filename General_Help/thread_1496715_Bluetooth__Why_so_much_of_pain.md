---
title: "Bluetooth : Why so much of pain ?"
date: 2010-05-29
forum: General Help
---

### Post by maxideci on 2010-05-29
Hello, 

I am having the problem enabling Bluetooth on my Dell studio 1555.

When I start System->Preference-Bluetooth Manager, I get message [i] Connection to Bluez failed : 
Bluez daemon is not running, blueman-manager cannot continue. [/i]

some information :

**uname -a **
Linux T-D 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux"

**hcitool dev **
Devices:
hci0 00:22:5F:97:20:A0"

**dmesg | grep 'Bluetooth'**
[    9.651122] Bluetooth: Core ver 2.15
[    9.651375] Bluetooth: HCI device and connection manager initialized
[    9.651378] Bluetooth: HCI socket layer initialized
[    9.692237] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  502.891750] Bluetooth: L2CAP ver 2.14
[  502.891755] Bluetooth: L2CAP socket layer initialized
[  503.021223] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  503.021228] Bluetooth: BNEP filters: protocol multicast
[  503.170048] Bluetooth: SCO (Voice Link) ver 0.6
[  503.170054] Bluetooth: SCO socket layer initialized
[  503.400998] Bluetooth: RFCOMM TTY layer initialized
[  503.401006] Bluetooth: RFCOMM socket layer initialized
[  503.401009] Bluetooth: RFCOMM ver 1.11

**lspci**
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

**lsusb**
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1733:0101 Cellink Technology Co., Ltd RF Wireless Optical Mouse OP-701
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63eb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**sudo bluetoothd -nd**
[sudo] password for esunny: 
bluetoothd[3182]: Bluetooth daemon 4.60
bluetoothd[3182]: Enabling debug information
bluetoothd[3182]: parsing main.conf
bluetoothd[3182]: discovto=0
bluetoothd[3182]: pairto=0
bluetoothd[3182]: pageto=8192
bluetoothd[3182]: name=%h-%d
bluetoothd[3182]: class=0x000100
bluetoothd[3182]: discov_interval=0
bluetoothd[3182]: Key file does not have key 'DeviceID'
bluetoothd[3182]: Starting SDP server
bluetoothd[3182]: binding L2CAP socket: Address already in use
bluetoothd[3182]: Server initialization failed
bluetoothd[3182]: Loading builtin plugins
bluetoothd[3182]: Loading audio plugin
bluetoothd[3182]: Loading input plugin
bluetoothd[3182]: Loading serial plugin
bluetoothd[3182]: Loading network plugin
bluetoothd[3182]: Loading service plugin
bluetoothd[3182]: Loading hciops plugin
bluetoothd[3182]: Loading storage plugin
bluetoothd[3182]: Loading plugins /usr/lib/bluetooth/plugins
bluetoothd[3182]: Loading netlink plugin
bluetoothd[3182]: register_interface: path /org/bluez/3182/any
bluetoothd[3182]: Registered interface org.bluez.Service on path /org/bluez/3182/any
bluetoothd[3182]: Starting experimental netlink support
bluetoothd[3182]: Failed to find Bluetooth netlink family
bluetoothd[3182]: Failed to init netlink plugin
bluetoothd[3182]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
bluetoothd[3182]: /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
bluetoothd[3182]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[3182]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[3182]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[3182]: Config options: InterfacePrefix=bnep%d, PANU_Script=(null), GN_Script=(null), NAP_Script=(null), GN_Interface=pan0, NAP_Interface=pan1, Security=true
bluetoothd[3182]: Can't create GN bridge
bluetoothd[3182]: input.conf: Key file does not have key 'IdleTimeout'
bluetoothd[3182]: Can't bind unix socket: Address already in use (98 )
bluetoothd[3182]: Unable to setup unix socket
bluetoothd[3182]: Failed to init audio plugin
bluetoothd[3182]: HCI dev 0 registered
bluetoothd[3182]: child 3184 forked
bluetoothd[3182]: btd_adapter_ref(0x7f32b133c2a0): ref=1
bluetoothd[3182]: HCI dev 0 up
bluetoothd[3182]: Starting security manager 0
bluetoothd[3182]: Changing Major/Minor class to 0x00010c
bluetoothd[3182]: Stopping Inquiry at adapter startup
bluetoothd[3182]: register_interface: path /org/bluez/3182/hci0
bluetoothd[3182]: Registered interface org.bluez.Service on path /org/bluez/3182/hci0
bluetoothd[3182]: network_server_probe: path /org/bluez/3182/hci0
bluetoothd[3182]: btd_adapter_ref(0x7f32b133c2a0): ref=2
bluetoothd[3182]: l2cap_bind: Address already in use (98 )
bluetoothd[3182]: btd_adapter_unref(0x7f32b133c2a0): ref=1
bluetoothd[3182]: network-panu-server: Invalid argument (22)
bluetoothd[3182]: network_server_probe: path /org/bluez/3182/hci0
bluetoothd[3182]: btd_adapter_ref(0x7f32b133c2a0): ref=2
bluetoothd[3182]: l2cap_bind: Address already in use (98 )
bluetoothd[3182]: btd_adapter_unref(0x7f32b133c2a0): ref=1
bluetoothd[3182]: network-gn-server: Invalid argument (22)
bluetoothd[3182]: network_server_probe: path /org/bluez/3182/hci0
bluetoothd[3182]: btd_adapter_ref(0x7f32b133c2a0): ref=2
bluetoothd[3182]: l2cap_bind: Address already in use (98 )
bluetoothd[3182]: btd_adapter_unref(0x7f32b133c2a0): ref=1
bluetoothd[3182]: network-nap-server: Invalid argument (22)
bluetoothd[3182]: proxy_probe: path /org/bluez/3182/hci0
bluetoothd[3182]: btd_adapter_ref(0x7f32b133c2a0): ref=2
bluetoothd[3182]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/3182/hci0
bluetoothd[3182]: Failed to listen on control channel
bluetoothd[3182]: input-server: Operation not permitted (1)
bluetoothd[3182]: Creating device /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96
bluetoothd[3182]: btd_device_ref(0x7f32b133d300): ref=1
bluetoothd[3182]: Probe drivers for /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00000002-0000-1000-8000-0002ee000002
bluetoothd[3182]: Registered interface org.bluez.Serial on path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00000004-0000-1000-8000-0002ee000002
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00001103-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00001105-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00001106-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00001112-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 0000111b-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 0000111f-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 0000112d-0000-1000-8000-00805f9b34fb
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00005005-0000-1000-8000-0002ee000001
bluetoothd[3182]: serial_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96: 00005601-0000-1000-8000-0002ee000001
bluetoothd[3182]: headset_probe: path /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96
bluetoothd[3182]: probe failed with driver input-headset for device /org/bluez/3182/hci0/dev_00_22_FD_62_E5_96
bluetoothd[3182]: Creating device /org/bluez/3182/hci0/dev_
00_22_FD_62_E5_96
bluetoothd[3182]: btd_device_ref(0x7f32b133c910): ref=1
bluetoothd[3182]: Adapter /org/bluez/3182/hci0 has been enabled
bluetoothd[3182]: Entering main loop
bluetoothd[3182]: Inquiry Failed with status 0x12
bluetoothd[3182]: child 3184 exited
bluetoothd[3182]: RFKILL event idx 0 type 2 op 0 soft 0 hard 0
bluetoothd[3182]: RFKILL event idx 1 type 1 op 0 soft 0 hard 0

**rfkill list**
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

I have reinstalled, removed rebooted and installed bluez, bluez-utils, Blueman, bluetooth number of times now.
Two attachments are included, 
[LIST=1]
[*]BlueZ output screen
[*]Bluetooth output screen
[/LIST]
Any idea how and what steps to take to debug the problem ? where exactly to look into.

Bluetooth works perfect, when I boot lucid using live CD, So I guess there is some problem with the installation. I upgraded from 9.10 to 10.4. It never worked with 9.10 and its continuing the same way.


Thanks,
Cheers!!

after a restart, I see bluetooth icon, but its grey all the time. two more screen shots..

[LIST=2]
[*]Bluetooth output screen (Turn on)
[*]Bluetooth output screen (Turned on)
[/LIST]

**sudo /etc/init.d/bluetooth status**
 * bluetooth is running

---

### Post by graphius on 2010-05-29
I was about to add my woes to this thread, but then I rebooted one more time, and now my bluetooth is working.
I still don't have an icon on my taskbar, but I can see my palm.

I did also try a 
> sudo apt-get purge bluez-utils  
then 
> sudo apt-get install bluez-utils 
before the reboot

---

### Post by maxideci on 2010-05-30
> **graphius said:**
> I was about to add my woes to this thread, but then I rebooted one more time, and now my bluetooth is working.
I still don't have an icon on my taskbar, but I can see my palm.

I did also try a 
  
then 
 
before the reboot

Lucky you, I believe things are just random with bluetooth working, I have searched so many forums and almost everyone has a different solution to it, there seemed to be no set procedure to it.

I once again booted from live lucid cd, and it worked like charm.

thanks for replying.

cheers!!

---

### Post by maxideci on 2010-05-30
As I mentioned earlier, I booted my system using live lucid cd, and bluetooth was working like charm.

some information form live cd.

**uname -a**
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

**hcitool dev**
Devices:
	hci0	00:22:5F:97:20:A0

**dmesg | grep 'Bluetooth'**
[   94.322468] Bluetooth: Core ver 2.15
[   94.323071] Bluetooth: HCI device and connection manager initialized
[   94.323074] Bluetooth: HCI socket layer initialized
[   94.389269] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   94.509439] Bluetooth: L2CAP ver 2.14
[   94.509441] Bluetooth: L2CAP socket layer initialized
[   94.539688] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   94.539691] Bluetooth: BNEP filters: protocol multicast
[   94.761675] Bluetooth: SCO (Voice Link) ver 0.6
[   94.761678] Bluetooth: SCO socket layer initialized
[   94.916850] Bluetooth: RFCOMM TTY layer initialized
[   94.916855] Bluetooth: RFCOMM socket layer initialized
[   94.916857] Bluetooth: RFCOMM ver 1.11

**lspci**
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
[COLOR="Red"]09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)[/COLOR]
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

**lsusb**
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1733:0101 Cellink Technology Co., Ltd RF Wireless Optical Mouse OP-701
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05dc:a813 Lexar Media, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63eb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**sudo bluetoothd -nd**
bluetoothd[4086]: Bluetooth daemon 4.60
bluetoothd[4086]: Enabling debug information
bluetoothd[4086]: parsing main.conf
bluetoothd[4086]: discovto=0
bluetoothd[4086]: pairto=0
bluetoothd[4086]: pageto=8192
bluetoothd[4086]: name=%h-%d
bluetoothd[4086]: class=0x000100
bluetoothd[4086]: discov_interval=0
bluetoothd[4086]: Key file does not have key 'DeviceID'
bluetoothd[4086]: Unable to get on D-Bus

**rfkill list**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

**sudo /etc/init.d/bluetooth status**
 * bluetooth is running

major difference I found was in the output of bluetoothd -nd command and also in the lspci output(in red).

thanks 
cheers!!

---

### Post by gradinaruvasile on 2010-05-30
It depends on the bluetooth hardware support in the kernel. I use a Dell D630 and the bluetooth works withouth problems. But i use blueman instead of the default Gnome bluetooth manager. Try it, it is far better.

---

### Post by maxideci on 2010-05-30
> **gradinaruvasile said:**
> It depends on the bluetooth hardware support in the kernel. I use a Dell D630 and the bluetooth works withouth problems. But i use blueman instead of the default Gnome bluetooth manager. Try it, it is far better.

I tried blueman to, but no luck, it throws errors 

>  Connection to Bluez failed :
Bluez daemon is not running, blueman-manager cannot continue.
Screenshot 1, from first post.

Cheers!!

---

### Post by spook45 on 2010-06-06
> **graphius said:**
> I was about to add my woes to this thread, but then I rebooted one more time, and now my bluetooth is working.
I still don't have an icon on my taskbar, but I can see my palm.

I did also try a 
  
then 
 
before the reboot

Tried this and it worked first time. I have a Dell Latitude running 10.04 and the latest kernel. Using bluez.

bob

---

### Post by maxideci on 2010-06-07
> **spook45 said:**
> Tried this and it worked first time. I have a Dell Latitude running 10.04 and the latest kernel. Using bluez.

bob

As I said, you guys are lucky ones...I actually gave up in a sense.

thanks though,

cheers!!

---

