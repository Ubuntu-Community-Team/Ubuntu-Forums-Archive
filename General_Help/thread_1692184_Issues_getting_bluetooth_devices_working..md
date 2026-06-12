---
title: "Issues getting bluetooth devices working."
date: 2011-02-21
forum: General Help
---

### Post by digitaldeviant2 on 2011-02-21
I was bored this Sunday, so I though I'd try to get my wii remote working with my Ubuntu desktop... I guess it's harder than I though.

Ubuntu reconizes my usb dongle:


Bus 002 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


But I can't get it to recognize my wii remote or my phone. I've looked at a bunch of 'How-to's' but I'm not getting anywhere. Anyone have any idea?

---

### Post by ignacio69 on 2011-02-23
I have the same problem:
cannot pair ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) in ubuntu 10.04
i have a USB Bluetooth dongle of the Cambridge Silicon Radio type, USB ID
0a12:0001. When I plug it into my  machine it's detected properly, Bluetooth services
are started, I get the icon in the system tray and everything. However,
scanning for devices - either using gnome-bluetooth's 'Set up new device...'
menu entry or 'hcitool scan' from a console - will not find any other device.
I verified that my NETBOOT RUNNING UBUNTU 9.04 and has a different
Bluetooth adapter) _does_ find these devices when I do a scan, so it's not
something wrong with the devices. The scan just isn't working for some reason.
hcitool scan doesn't return an error - it says 'Scanning ...', waits a while,
then goes back to the console, just as you'd expect if there were nothing to
find.


here is the output: 
lsusb
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

cat /proc/bus/usb/devices  | more
cat: /proc/bus/usb/devices: No existe el fichero o el directorio

lsmod | more
Module                  Size  Used by
xt_limit                1382  8 
xt_tcpudp               2011  7 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
rfcomm                 33421  8 
binfmt_misc             6587  1 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
snd_hda_codec_via      27111  1 
l2cap                  30624  16 rfcomm,bnep
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat
nf_conntrack           61615  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp
,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 

hciconfig -a
hci0:	Type: USB
	BD Address: 00:15:83:3D:0A:57 ACL MTU: 310:10 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:967 acl:0 sco:0 events:28 errors:0
	TX bytes:367 acl:0 sco:0 commands:28 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'ignacio-desktop-0'
	Class: 0x5a0100
	Service Classes: Networking, Capturing, Object Transfer, Telephony
	Device Class: Computer, Uncategorized
	HCI Ver: 2.0 (0x3) HCI Rev: 0xc5c LMP Ver: 2.0 (0x3) LMP Subver: 0xc5c
	Manufacturer: Cambridge Silicon Radio (10)

dmesg
[   20.954383] Bluetooth: L2CAP ver 2.14
[   20.954387] Bluetooth: L2CAP socket layer initialized
[   21.052328] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.052331] Bluetooth: BNEP filters: protocol multicast
[   21.259422] Bluetooth: SCO (Voice Link) ver 0.6
[   21.259429] Bluetooth: SCO socket layer initialized
[   21.732672] Bluetooth: RFCOMM TTY layer initialized
[   21.732682] Bluetooth: RFCOMM socket layer initialized
[   21.732688] Bluetooth: RFCOMM ver 1.11
hcitool dev
Devices:
	hci0	00:15:83:3D:0A:57
hcitool scan
Scanning ...
sudo hcitool cc 00:15:83:3D:0A:57
Device is not available.

---

### Post by ignacio69 on 2011-03-06
Dear all,
the bluetooth adapter ID 0a12:0001 Cambridge Silicon Radio, is working,
however it cannot connect to my headseat NOKIA BH-104.
here is the output when trying:
dmessage:
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.419540] Bluetooth: Core ver 2.15
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.420017] Bluetooth: HCI device and connection manager initialized
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.420020] Bluetooth: HCI socket layer initialized
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.667339] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.153977] Bluetooth: L2CAP ver 2.14
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.153981] Bluetooth: L2CAP socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.223534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.223542] Bluetooth: BNEP filters: protocol multicast
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.394353] Bluetooth: SCO (Voice Link) ver 0.6
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.394356] Bluetooth: SCO socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775342] Bluetooth: RFCOMM TTY layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775348] Bluetooth: RFCOMM socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775351] Bluetooth: RFCOMM ver 1.11
debug:
Mar 5 19:23:07 ignacio-desktop bluetoothd[954]: Bluetooth daemon 4.60
Mar 5 19:23:08 ignacio-desktop bluetoothd[1143]: Failed to find Bluetooth netlink family
kern.log:
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.419540] Bluetooth: Core ver 2.15
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.420017] Bluetooth: HCI device and connection manager initialized
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.420020] Bluetooth: HCI socket layer initialized
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.667339] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.153977] Bluetooth: L2CAP ver 2.14
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.153981] Bluetooth: L2CAP socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.223534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.223542] Bluetooth: BNEP filters: protocol multicast
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.394353] Bluetooth: SCO (Voice Link) ver 0.6
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.394356] Bluetooth: SCO socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775342] Bluetooth: RFCOMM TTY layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775348] Bluetooth: RFCOMM socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775351] Bluetooth: RFCOMM ver 1.11
syslog:
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.419540] Bluetooth: Core ver 2.15
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.420017] Bluetooth: HCI device and connection manager initialized
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.420020] Bluetooth: HCI socket layer initialized
Mar 5 19:23:07 ignacio-desktop kernel: [ 21.667339] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar 5 19:23:07 ignacio-desktop bluetoothd[954]: Bluetooth daemon 4.60
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.153977] Bluetooth: L2CAP ver 2.14
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.153981] Bluetooth: L2CAP socket layer initialized
Mar 5 19:23:08 ignacio-desktop bluetoothd[1143]: Failed to find Bluetooth netlink family
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.223534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.223542] Bluetooth: BNEP filters: protocol multicast
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.394353] Bluetooth: SCO (Voice Link) ver 0.6
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.394356] Bluetooth: SCO socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775342] Bluetooth: RFCOMM TTY layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775348] Bluetooth: RFCOMM socket layer initialized
Mar 5 19:23:08 ignacio-desktop kernel: [ 22.775351] Bluetooth: RFCOMM ver 1.11

can anybody help?
do I need to set something else?

---

