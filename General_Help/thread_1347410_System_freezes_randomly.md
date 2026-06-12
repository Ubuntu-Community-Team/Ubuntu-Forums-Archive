---
title: "System freezes randomly"
date: 2009-12-06
forum: General Help
---

### Post by randomguy1 on 2009-12-06
Hello,
I've been having system freezes since im running ubuntu on this computer.
When my pc freezes i cannot move the mouse or  use the keyboard and the Scroll Lock and the Caps lock lights begin to flash. Then I have to turn off the power switch to restart.
The freezes occur completly random and are not really frequent, like once per day or so.
Im running 9.10 and the freezes occured with Kernel 2.6.31-14-generic aswell as with Kernel 2.6.31-15-generic. Only difference is that on 2.6.31-14-generic, everytime the caps lock and the scroll lock lights fash i get an error sound, on 2.6.31-15-generic the lights flash silently.

At the last freeze my screen froze at 12:16, so i figured this logs might contain the solution to my problem:

debug.1:
```
Dec  6 11:15:59 jan-desktop kernel: [ 1392.966134] /dev/vmmon[5009]: Module vmmon: registered with major=10 minor=165
Dec  6 11:15:59 jan-desktop kernel: [ 1392.966144] /dev/vmmon[5009]: Module vmmon: initialized
Dec  6 11:15:59 jan-desktop kernel: [ 1392.981042] /dev/vmci[5017]: VMCI: Driver initialized.
Dec  6 11:15:59 jan-desktop kernel: [ 1392.981132] /dev/vmci[5017]: Module vmci: registered with major=10 minor=54
Dec  6 11:15:59 jan-desktop kernel: [ 1392.981135] /dev/vmci[5017]: Module vmci: initialized
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094300] /dev/vmnet: open called by PID 5067 (vmnet-bridge)
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094314] /dev/vmnet: hub 0 does not exist, allocating memory.
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094340] /dev/vmnet: port on hub 0 successfully opened
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094367] bridge-wlan0: up
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094372] bridge-wlan0: attached
Dec  6 11:16:00 jan-desktop kernel: [ 1394.123741] /dev/vmnet: open called by PID 5074 (vmnet-dhcpd)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.123757] /dev/vmnet: hub 1 does not exist, allocating memory.
Dec  6 11:16:00 jan-desktop kernel: [ 1394.123793] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.126948] /dev/vmnet: open called by PID 5076 (vmnet-netifup)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.126973] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.145042] /dev/vmnet: open called by PID 5080 (vmnet-dhcpd)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.145060] /dev/vmnet: hub 8 does not exist, allocating memory.
Dec  6 11:16:00 jan-desktop kernel: [ 1394.145095] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.152404] /dev/vmnet: open called by PID 5084 (vmnet-natd)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.152428] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.157072] /dev/vmnet: open called by PID 5085 (vmnet-netifup)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.157099] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.281237] bridge-wlan0: disabling the bridge
Dec  6 11:16:00 jan-desktop kernel: [ 1394.311696] bridge-wlan0: down
Dec  6 11:16:00 jan-desktop kernel: [ 1394.311716] bridge-wlan0: detached
Dec  6 11:16:18 jan-desktop kernel: [ 1412.218244] /dev/vmci[5149]: Module vmci: unloaded
Dec  6 11:16:18 jan-desktop kernel: [ 1412.230670] /dev/vmmon[5158]: Module vmmon: unloaded
Dec  6 11:16:18 jan-desktop kernel: [ 1412.377715] /dev/vmmon[5197]: Module vmmon: registered with major=10 minor=165
Dec  6 11:16:18 jan-desktop kernel: [ 1412.377725] /dev/vmmon[5197]: Module vmmon: initialized
Dec  6 11:16:18 jan-desktop kernel: [ 1412.402592] /dev/vmci[5205]: VMCI: Driver initialized.
Dec  6 11:16:18 jan-desktop kernel: [ 1412.402683] /dev/vmci[5205]: Module vmci: registered with major=10 minor=54
Dec  6 11:16:18 jan-desktop kernel: [ 1412.402687] /dev/vmci[5205]: Module vmci: initialized
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527128] /dev/vmnet: open called by PID 5246 (vmnet-bridge)
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527143] /dev/vmnet: hub 0 does not exist, allocating memory.
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527177] /dev/vmnet: port on hub 0 successfully opened
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527207] bridge-wlan0: up
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527213] bridge-wlan0: attached
Dec  6 11:16:21 jan-desktop kernel: [ 1414.569614] /dev/vmnet: open called by PID 5253 (vmnet-dhcpd)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.569631] /dev/vmnet: hub 1 does not exist, allocating memory.
Dec  6 11:16:21 jan-desktop kernel: [ 1414.569665] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.572942] /dev/vmnet: open called by PID 5255 (vmnet-netifup)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.572967] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.587088] /dev/vmnet: open called by PID 5257 (vmnet-dhcpd)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.587107] /dev/vmnet: hub 8 does not exist, allocating memory.
Dec  6 11:16:21 jan-desktop kernel: [ 1414.587142] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.601297] /dev/vmnet: open called by PID 5261 (vmnet-natd)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.601320] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.605155] /dev/vmnet: open called by PID 5262 (vmnet-netifup)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.605182] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:31 jan-desktop kernel: [ 1425.120012] vmnet1: no IPv6 routers present
Dec  6 11:16:31 jan-desktop kernel: [ 1425.430013] vmnet8: no IPv6 routers present
```and kern.log.1:

```
Dec  6 11:15:59 jan-desktop kernel: [ 1392.966134] /dev/vmmon[5009]: Module vmmon: registered with major=10 minor=165
Dec  6 11:15:59 jan-desktop kernel: [ 1392.966144] /dev/vmmon[5009]: Module vmmon: initialized
Dec  6 11:15:59 jan-desktop kernel: [ 1392.981042] /dev/vmci[5017]: VMCI: Driver initialized.
Dec  6 11:15:59 jan-desktop kernel: [ 1392.981132] /dev/vmci[5017]: Module vmci: registered with major=10 minor=54
Dec  6 11:15:59 jan-desktop kernel: [ 1392.981135] /dev/vmci[5017]: Module vmci: initialized
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094300] /dev/vmnet: open called by PID 5067 (vmnet-bridge)
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094314] /dev/vmnet: hub 0 does not exist, allocating memory.
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094340] /dev/vmnet: port on hub 0 successfully opened
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094360] bridge-wlan0: is a Wireless Adapter
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094367] bridge-wlan0: up
Dec  6 11:15:59 jan-desktop kernel: [ 1393.094372] bridge-wlan0: attached
Dec  6 11:16:00 jan-desktop kernel: [ 1394.123741] /dev/vmnet: open called by PID 5074 (vmnet-dhcpd)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.123757] /dev/vmnet: hub 1 does not exist, allocating memory.
Dec  6 11:16:00 jan-desktop kernel: [ 1394.123793] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.126948] /dev/vmnet: open called by PID 5076 (vmnet-netifup)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.126973] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.145042] /dev/vmnet: open called by PID 5080 (vmnet-dhcpd)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.145060] /dev/vmnet: hub 8 does not exist, allocating memory.
Dec  6 11:16:00 jan-desktop kernel: [ 1394.145095] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.152404] /dev/vmnet: open called by PID 5084 (vmnet-natd)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.152428] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.157072] /dev/vmnet: open called by PID 5085 (vmnet-netifup)
Dec  6 11:16:00 jan-desktop kernel: [ 1394.157099] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:00 jan-desktop kernel: [ 1394.281237] bridge-wlan0: disabling the bridge
Dec  6 11:16:00 jan-desktop kernel: [ 1394.311696] bridge-wlan0: down
Dec  6 11:16:00 jan-desktop kernel: [ 1394.311716] bridge-wlan0: detached
Dec  6 11:16:18 jan-desktop kernel: [ 1412.218244] /dev/vmci[5149]: Module vmci: unloaded
Dec  6 11:16:18 jan-desktop kernel: [ 1412.230670] /dev/vmmon[5158]: Module vmmon: unloaded
Dec  6 11:16:18 jan-desktop kernel: [ 1412.377715] /dev/vmmon[5197]: Module vmmon: registered with major=10 minor=165
Dec  6 11:16:18 jan-desktop kernel: [ 1412.377725] /dev/vmmon[5197]: Module vmmon: initialized
Dec  6 11:16:18 jan-desktop kernel: [ 1412.402592] /dev/vmci[5205]: VMCI: Driver initialized.
Dec  6 11:16:18 jan-desktop kernel: [ 1412.402683] /dev/vmci[5205]: Module vmci: registered with major=10 minor=54
Dec  6 11:16:18 jan-desktop kernel: [ 1412.402687] /dev/vmci[5205]: Module vmci: initialized
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527128] /dev/vmnet: open called by PID 5246 (vmnet-bridge)
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527143] /dev/vmnet: hub 0 does not exist, allocating memory.
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527177] /dev/vmnet: port on hub 0 successfully opened
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527200] bridge-wlan0: is a Wireless Adapter
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527207] bridge-wlan0: up
Dec  6 11:16:20 jan-desktop kernel: [ 1413.527213] bridge-wlan0: attached
Dec  6 11:16:21 jan-desktop kernel: [ 1414.569614] /dev/vmnet: open called by PID 5253 (vmnet-dhcpd)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.569631] /dev/vmnet: hub 1 does not exist, allocating memory.
Dec  6 11:16:21 jan-desktop kernel: [ 1414.569665] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.572942] /dev/vmnet: open called by PID 5255 (vmnet-netifup)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.572967] /dev/vmnet: port on hub 1 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.587088] /dev/vmnet: open called by PID 5257 (vmnet-dhcpd)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.587107] /dev/vmnet: hub 8 does not exist, allocating memory.
Dec  6 11:16:21 jan-desktop kernel: [ 1414.587142] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.601297] /dev/vmnet: open called by PID 5261 (vmnet-natd)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.601320] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:21 jan-desktop kernel: [ 1414.605155] /dev/vmnet: open called by PID 5262 (vmnet-netifup)
Dec  6 11:16:21 jan-desktop kernel: [ 1414.605182] /dev/vmnet: port on hub 8 successfully opened
Dec  6 11:16:31 jan-desktop kernel: [ 1425.120012] vmnet1: no IPv6 routers present
Dec  6 11:16:31 jan-desktop kernel: [ 1425.430013] vmnet8: no IPv6 routers present
```And here's a system report from the "System Profiler and Benchmark" app:

```

Computer
********


Summary
-------

-Computer-
Processor        : 2x Genuine Intel(R) CPU            2140  @ 1.60GHz
Memory        : 5091MB (3582MB used)
Operating System        : Ubuntu 9.10
User Name        : jan (jan)
Date/Time        : Sun 06 Dec 2009 12:52:49 PM CET
-Display-
Resolution        : 1680x1050 pixels
OpenGL Renderer        : GeForce GTX 260/PCI/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA ATI SB
-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Logitech USB-PS/2 Optical Mouse
 HDA Digital PCBeep
-Printers-
No printers found
-SCSI Disks-
ATA HDT722525DLA380
ATAPI DVD W  DH16W1P
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader
Generic USB MS Reader

Operating System
----------------

-Version-
Kernel        : Linux 2.6.31-15-generic (x86_64)
Compiled        : #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009
C Library        : GNU C Library version 2.10.1 (stable)
Default C Compiler        : GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
Distribution        : Ubuntu 9.10
-Current Session-
Computer Name        : jan-desktop
User Name        : jan (jan)
Home Directory        : /home/jan
Desktop Environment        : GNOME 2.28.1
-Misc-
Uptime        : 29 minutes
Load Average        : 2.95, 2.52, 1.82

Kernel Modules
--------------

-Loaded Modules-
isofs
udf        : Universal Disk Format Filesystem
crc_itu_t        : CRC ITU-T V.41 calculations
binfmt_misc
vboxnetflt        : VirtualBox Network Filter Driver
vboxnetadp        : VirtualBox Network Adapter Driver
vboxdrv        : VirtualBox Support Driver
snd_hda_codec_realtek        : Realtek HD-audio codec
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
snd_hwdep        : Hardware dependent layer
snd_pcm_oss        : PCM OSS emulation for ALSA.
snd_mixer_oss        : Mixer OSS emulation for ALSA.
snd_pcm        : Midlevel PCM code for ALSA.
coretemp        : Intel Core temperature monitor
snd_seq_dummy        : ALSA sequencer MIDI-through client
snd_seq_oss        : OSS-compatible sequencer module
it87        : IT8705F/8712F/8716F/8718F/8720F/8726F, SiS950 driver
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
hwmon_vid        : hwmon-vid driver
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_timer        : ALSA timer interface
snd_seq_device        : ALSA sequencer device management
iptable_filter        : iptables filter table
snd        : Advanced Linux Sound Architecture driver for soundcards.
ip_tables        : IPv4 packet filter
ppdev
soundcore        : Core sound module
lp
snd_page_alloc        : Memory allocator for ALSA system.
parport_pc        : PC-style parallel port driver
i2c_piix4        : PIIX4 SMBus driver
x_tables        : {ip,ip6,arp,eb}_tables backend module
nvidia
parport
led_class        : LED Class Interface
ndiswrapper        : NDIS wrapper driver
usbhid        : USB HID core driver
usb_storage        : USB Mass Storage driver for Linux
ohci1394        : Driver for PCI OHCI IEEE-1394 controllers
floppy
ieee1394
sky2        : Marvell Yukon 2 Gigabit Ethernet driver

Boots
-----

-Boots-
Sun Dec 6 12:23        : 2.6.31-15-generi|-
Sun Dec 6 11:49        : 2.6.31-15-generi|-
Sun Dec 6 10:53        : 2.6.31-15-generi|-
Sat Dec 5 23:24        : 2.6.31-15-generi|-
Sat Dec 5 13:43        : 2.6.31-15-generi|-
Sat Dec 5 12:40        : 2.6.31-15-generi|-
Sat Dec 5 09:37        : 2.6.31-15-generi|-
Fri Dec 4 19:24        : 2.6.31-15-generi|-
Fri Dec 4 13:35        : 2.6.31-15-generi|-
Thu Dec 3 18:52        : 2.6.31-15-generi|-
Thu Dec 3 18:50        : 2.6.31-15-generi|-
Thu Dec 3 18:47        : 2.6.31-15-generi|-
Thu Dec 3 18:47        : 2.6.31-15-generi|-
Thu Dec 3 18:41        : 2.6.31-15-generi|-
Thu Dec 3 18:40        : 2.6.31-15-server|-
Thu Dec 3 18:29        : 2.6.31-15-generi|-
Thu Dec 3 18:23        : 2.6.31-14-generi|-
Thu Dec 3 18:22        : 2.6.31-15-server|-
Thu Dec 3 18:21        : 2.6.31-15-server|-
Thu Dec 3 18:20        : 2.6.31-15-server|-
Thu Dec 3 17:58        : 2.6.31-14-generi|-
Thu Dec 3 17:57        : 2.6.31-15-server|-
Thu Dec 3 17:52        : 2.6.31-14-generi|-
Thu Dec 3 17:51        : 2.6.31-15-server|-
Thu Dec 3 17:42        : 2.6.31-14-generi|-
Thu Dec 3 17:41        : 2.6.31-15-server|-
Thu Dec 3 17:37        : 2.6.31-14-generi|-
Thu Dec 3 17:36        : 2.6.31-15-server|-
Thu Dec 3 16:30        : 2.6.31-14-generi|-
Thu Dec 3 16:12        : 2.6.31-15-server|-
Thu Dec 3 16:08        : 2.6.31-14-generi|-
Thu Dec 3 16:07        : 2.6.31-15-server|-
Thu Dec 3 16:05        : 2.6.31-15-server|-
Thu Dec 3 16:03        : 2.6.31-15-generi|-
Thu Dec 3 14:58        : 2.6.31-14-generi|-
Thu Dec 3 12:55        : 2.6.31-14-generi|-
Wed Dec 2 19:52        : 2.6.31-14-generi|-
Wed Dec 2 14:27        : 2.6.31-14-generi|-

Languages
---------

-Available Languages-
en_AG        : English language locale for Antigua and Barbuda
en_AU.utf8        : English locale for Australia
en_BW.utf8        : English locale for Botswana
en_CA.utf8        : English locale for Canada
en_DK.utf8        : English locale for Denmark
en_GB.utf8        : English locale for Britain
en_HK.utf8        : English locale for Hong Kong
en_IE.utf8        : English locale for Ireland
en_IN        : English language locale for India
en_NG        : English locale for Nigeria
en_NZ.utf8        : English locale for New Zealand
en_PH.utf8        : English language locale for Philippines
en_SG.utf8        : English language locale for Singapore
en_US.utf8        : English locale for the USA
en_ZA.utf8        : English locale for South Africa

Filesystems
-----------

-Mounted File Systems-
/dev/sda1    /    49.52 % (111.0 GiB of 219.9 GiB)    
udev    /dev    0.01 % (2.4 GiB of 2.4 GiB)    
none    /dev/shm    0.38 % (2.4 GiB of 2.4 GiB)    
none    /var/run    0.01 % (2.4 GiB of 2.4 GiB)    
none    /var/lock    0.00 % (2.4 GiB of 2.4 GiB)    
none    /lib/init/rw    0.00 % (2.4 GiB of 2.4 GiB)    
none    /var/lib/ureadahead/debugfs    49.52 % (111.0 GiB of 219.9 GiB)    
/dev/sr0    /media/cdrom0    100.00 % (0.0 B of 2.8 GiB)    

Display
-------

-Display-
Resolution        : 1680x1050 pixels
Vendor        : The X.Org Foundation
Version        : 1.6.4
-Monitors-
Monitor 0        : 1680x1050 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : NVIDIA Corporation
Renderer        : GeForce GTX 260/PCI/SSE2
Version        : 3.0.0 NVIDIA 185.18.36
Direct Rendering        : Yes

Environment Variables
---------------------

-Environment Variables-
GDM_KEYBOARD_LAYOUT        : de
USER        : jan
SSH_AGENT_PID        : 1917
HOME        : /home/jan
DESKTOP_SESSION        : gnome
XDG_SESSION_COOKIE        : a26baefddde27a1e7f37eda64ae5efb6-1260098623.497184-1598980627
GTK_MODULES        : canberra-gtk-module
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-ocQSg2xFxW,guid=d1e90736954682a659ba2f504b1b9444
LOGNAME        : jan
USERNAME        : jan
GDM_LANG        : en_US.UTF-8
PATH        : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DISPLAY        : :0.0
LANG        : en_US.UTF-8
XAUTHORITY        : /var/run/gdm/auth-for-jan-ERiD71/database
SSH_AUTH_SOCK        : /tmp/keyring-j3V6ec/socket.ssh
SHELL        : /bin/bash
GDMSESSION        : gnome
PWD        : /home/jan
SPEECHD_PORT        : 7560
XDG_DATA_DIRS        : /usr/share/gnome:/usr/local/share/:/usr/share/
GPG_AGENT_INFO        : /tmp/seahorse-Il3yXw/S.gpg-agent:1940:1
GNOME_DESKTOP_SESSION_ID        : this-is-deprecated
SESSION_MANAGER        : local/jan-desktop:@/tmp/.ICE-unix/1841,unix/jan-desktop:/tmp/.ICE-unix/1841
ORBIT_SOCKETDIR        : /tmp/orbit-jan
GTK_RC_FILES        : /etc/gtk/gtkrc:/home/jan/.gtkrc-1.2-gnome2
GNOME_KEYRING_SOCKET        : /tmp/keyring-j3V6ec/socket

Users
-----

-Users-
root        : root
daemon        : daemon
bin        : bin
sys        : sys
sync        : sync
games        : games
man        : man
lp        : lp
mail        : mail
news        : news
uucp        : uucp
proxy        : proxy
www-data        : www-data
backup        : backup
list        : Mailing List Manager
irc        : ircd
gnats        : Gnats Bug-Reporting System (admin)
nobody        : nobody
libuuid
syslog
klog
hplip        : HPLIP system user
avahi-autoipd        : Avahi autoip daemon
gdm        : Gnome Display Manager
saned
pulse        : PulseAudio daemon
messagebus
polkituser        : PolicyKit
avahi        : Avahi mDNS daemon
haldaemon        : Hardware abstraction layer
jan        : jan
speech-dispatcher        : Speech Dispatcher
couchdb        : CouchDB Administrator
kernoops        : Kernel Oops Tracking Daemon
timidity        : TiMidity++ MIDI sequencer service
festival

Devices
*******


Processor
---------

-Processors-
Genuine Intel(R) CPU            2140  @ 1.60GHz        : 1200.00MHz
Genuine Intel(R) CPU            2140  @ 1.60GHz        : 1600.00MHz

Memory
------

-Memory-
Total Memory        : 5091372 kB
Free Memory        : 40532 kB
Buffers        : 871000 kB
Cached        : 1468688 kB
Cached Swap        : 924 kB
Active        : 2037132 kB
Inactive        : 2288144 kB
Active(anon)        : 1600736 kB
Inactive(anon)        : 400120 kB
Active(file)        : 436396 kB
Inactive(file)        : 1888024 kB
Unevictable        : 520 kB
Mlocked        : 520 kB
Virtual Memory        : 9936160 kB
Free Virtual Memory        : 9934184 kB
Dirty        : 12856 kB
Writeback        : 0 kB
AnonPages        : 1985480 kB
Mapped        : 292644 kB
Slab        : 143788 kB
SReclaimable        : 110016 kB
SUnreclaim        : 33772 kB
PageTables        : 24976 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 12481844 kB
Committed_AS        : 2811600 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 332416 kB
VmallocChunk        : 34359404955 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 70528 kB
DirectMap2M        : 5171200 kB

PCI Devices
-----------

-PCI Devices-
Host bridge        : ATI Technologies Inc Radeon Xpress 7930 Host Bridge
PCI bridge        : ATI Technologies Inc RS7933 PCI Bridge
PCI bridge        : ATI Technologies Inc RS7936 PCI Bridge
SATA controller        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
USB Controller        : ATI Technologies Inc SB600 USB 
USB Controller        : ATI Technologies Inc SB600 USB 
USB Controller        : ATI Technologies Inc SB600 USB 
USB Controller        : ATI Technologies Inc SB600 USB 
USB Controller        : ATI Technologies Inc SB600 USB 
USB Controller        : ATI Technologies Inc SB600 USB Controller 
SMBus        : ATI Technologies Inc SBx00 SMBus Controller 
IDE interface        : ATI Technologies Inc SB600 IDE 
Audio device        : ATI Technologies Inc SBx00 Azalia 
ISA bridge        : ATI Technologies Inc SB600 PCI to LPC Bridge
PCI bridge        : ATI Technologies Inc SBx00 PCI to PCI Bridge 
VGA compatible controller        : nVidia Corporation GT200 [GeForce GTX 260] 
Ethernet controller        : Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller 
FireWire (IEEE 1394)        : Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller 

USB Devices
-----------


Printers
--------

-Printers-
No printers found

Battery
-------

-No batteries-
No batteries found on this system

Sensors
-------

-ACPI Thermal Zone-
THRM        : -127°C

Input Devices
-------------

-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Logitech USB-PS/2 Optical Mouse
 HDA Digital PCBeep

Storage
-------

-SCSI Disks-
ATA HDT722525DLA380
ATAPI DVD W  DH16W1P
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader
Generic USB MS Reader

DMI
---

-BIOS-
Date        : 03/06/2007
Vendor        : Phoenix Technologies, LTD
Version        : R01-A4
-Board-
Name        : MRS600M
Vendor        : Acer

Resources
---------

-I/O Ports-
<tt>0000-001f </tt>        : dma1
<tt>0020-0021 </tt>        : pic1
<tt>0040-0043 </tt>        : timer0
<tt>0050-0053 </tt>        : timer1
<tt>0060-0060 </tt>        : keyboard
<tt>0064-0064 </tt>        : keyboard
<tt>0070-0073 </tt>        : rtc0
<tt>0080-008f </tt>        : dma page reg
<tt>00a0-00a1 </tt>        : pic2
<tt>00c0-00df </tt>        : dma2
<tt>00f0-00ff </tt>        : fpu
<tt>0170-0177 </tt>        : ATI Technologies Inc SB600 IDE 
<tt>  0170-0177 </tt>        : pata_atiixp
<tt>01f0-01f7 </tt>        : ATI Technologies Inc SB600 IDE 
<tt>  01f0-01f7 </tt>        : pata_atiixp
<tt>0228-022f </tt>        : pnp 00:01
<tt>  022d-022e </tt>        : IT8705F/8712F/8716F/8718F/8720F/8726F, SiS950 driver
<tt>    022d-022e </tt>        : IT8705F/8712F/8716F/8718F/8720F/8726F, SiS950 driver
<tt>0376-0376 </tt>        : ATI Technologies Inc SB600 IDE 
<tt>  0376-0376 </tt>        : pata_atiixp
<tt>0378-037a </tt>        : parport0
<tt>03c0-03df </tt>        : vga+
<tt>03f2-03f2 </tt>        : floppy
<tt>03f4-03f5 </tt>        : floppy
<tt>03f6-03f6 </tt>        : ATI Technologies Inc SB600 IDE 
<tt>  03f6-03f6 </tt>        : pata_atiixp
<tt>03f7-03f7 </tt>        : floppy
<tt>03f8-03ff </tt>        : serial
<tt>040b-040b </tt>        : pnp 00:01
<tt>04d0-04d1 </tt>        : pnp 00:08
<tt>04d6-04d6 </tt>        : pnp 00:01
<tt>0800-0805 </tt>        : pnp 00:08
<tt>0880-088f </tt>        : pnp 00:08
<tt>0b00-0b0f </tt>        : ATI Technologies Inc SBx00 SMBus Controller 
<tt>  0b00-0b07 </tt>        : piix4_smbus
<tt>0b10-0b1f </tt>        : pnp 00:01
<tt>0c00-0c01 </tt>        : pnp 00:01
<tt>0c14-0c14 </tt>        : pnp 00:01
<tt>0c50-0c52 </tt>        : pnp 00:01
<tt>0c6c-0c6d </tt>        : pnp 00:01
<tt>0c6f-0c6f </tt>        : pnp 00:01
<tt>0cd0-0cd1 </tt>        : pnp 00:01
<tt>0cd2-0cd3 </tt>        : pnp 00:01
<tt>0cd4-0cdf </tt>        : pnp 00:01
<tt>0cf8-0cff </tt>        : PCI conf1
<tt>4000-40fe </tt>        : pnp 00:01
<tt>  4000-4003 </tt>        : ACPI PM1a_EVT_BLK
<tt>  4004-4005 </tt>        : ACPI PM1a_CNT_BLK
<tt>  4008-400b </tt>        : ACPI PM_TMR
<tt>  4010-4015 </tt>        : ACPI CPU throttle
<tt>  4020-4027 </tt>        : ACPI GPE0_BLK
<tt>  4050-4050 </tt>        : ACPI PM2_CNT_BLK
<tt>4100-411f </tt>        : pnp 00:01
<tt>4210-4217 </tt>        : pnp 00:01
<tt>c000-cfff </tt>        : PCI Bus 0000:03
<tt>d000-dfff </tt>        : PCI Bus 0000:01
<tt>  df00-df7f </tt>        : nVidia Corporation GT200 [GeForce GTX 260] 
<tt>e000-efff </tt>        : PCI Bus 0000:02
<tt>  ee00-eeff </tt>        : Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller 
<tt>    ee00-eeff </tt>        : Marvell Yukon 2 Gigabit Ethernet driver
<tt>f900-f90f </tt>        : ATI Technologies Inc SB600 IDE 
<tt>  f900-f90f </tt>        : pata_atiixp
<tt>fb00-fb0f </tt>        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
<tt>  fb00-fb0f </tt>        : ahci
<tt>fc00-fc03 </tt>        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
<tt>  fc00-fc03 </tt>        : ahci
<tt>fd00-fd07 </tt>        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
<tt>  fd00-fd07 </tt>        : ahci
<tt>fe00-fe03 </tt>        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
<tt>  fe00-fe03 </tt>        : ahci
<tt>ff00-ff07 </tt>        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
<tt>  ff00-ff07 </tt>        : ahci
-Memory-
<tt>00000000-0000ffff </tt>        : reserved
<tt>00010000-0009f3ff </tt>        : System RAM
<tt>0009f400-0009ffff </tt>        : reserved
<tt>000f0000-000fffff </tt>        : reserved
<tt>00100000-cfedffff </tt>        : System RAM
<tt>  01000000-01530d98 </tt>        : Kernel code
<tt>  01530d99-018236af </tt>        : Kernel data
<tt>  018d5000-019e4ccb </tt>        : Kernel bss
<tt>cfee0000-cfee2fff </tt>        : ACPI Non-volatile Storage
<tt>cfee3000-cfeeffff </tt>        : ACPI Tables
<tt>cfef0000-cfefffff </tt>        : reserved
<tt>cff00000-cfffffff </tt>        : RAM buffer
<tt>d0000000-dfffffff </tt>        : PCI Bus 0000:01
<tt>  d0000000-dfffffff </tt>        : nVidia Corporation GT200 [GeForce GTX 260] 
<tt>e0000000-efffffff </tt>        : PCI MMCONFIG 0 [00-ff]
<tt>  e0000000-efffffff </tt>        : reserved
<tt>    e0000000-efffffff </tt>        : pnp 00:0d
<tt>f8000000-fbffffff </tt>        : PCI Bus 0000:01
<tt>  f8000000-f9ffffff </tt>        : nVidia Corporation GT200 [GeForce GTX 260] 
<tt>  fa000000-faffffff </tt>        : nVidia Corporation GT200 [GeForce GTX 260] 
<tt>    fa000000-faffffff </tt>        : nvidia
<tt>  fb000000-fb07ffff </tt>        : nVidia Corporation GT200 [GeForce GTX 260] 
<tt>fdb00000-fdbfffff </tt>        : PCI Bus 0000:03
<tt>fdc00000-fdcfffff </tt>        : PCI Bus 0000:03
<tt>  fdcf8000-fdcfbfff </tt>        : Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller 
<tt>  fdcff000-fdcff7ff </tt>        : Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller 
<tt>    fdcff000-fdcff7ff </tt>        : Driver for PCI OHCI IEEE-1394 controllers
<tt>fdd00000-fddfffff </tt>        : PCI Bus 0000:02
<tt>  fddfc000-fddfffff </tt>        : Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller 
<tt>    fddfc000-fddfffff </tt>        : Marvell Yukon 2 Gigabit Ethernet driver
<tt>fde00000-fdefffff </tt>        : PCI Bus 0000:02
<tt>  fde00000-fde1ffff </tt>        : Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller 
<tt>fdff4000-fdff7fff </tt>        : ATI Technologies Inc SBx00 Azalia 
<tt>  fdff4000-fdff7fff </tt>        : ICH HD audio
<tt>fdff9000-fdff90ff </tt>        : ATI Technologies Inc SB600 USB Controller 
<tt>  fdff9000-fdff90ff </tt>        : ehci_hcd
<tt>fdffa000-fdffafff </tt>        : ATI Technologies Inc SB600 USB 
<tt>  fdffa000-fdffafff </tt>        : ohci_hcd
<tt>fdffb000-fdffbfff </tt>        : ATI Technologies Inc SB600 USB 
<tt>  fdffb000-fdffbfff </tt>        : ohci_hcd
<tt>fdffc000-fdffcfff </tt>        : ATI Technologies Inc SB600 USB 
<tt>  fdffc000-fdffcfff </tt>        : ohci_hcd
<tt>fdffd000-fdffdfff </tt>        : ATI Technologies Inc SB600 USB 
<tt>  fdffd000-fdffdfff </tt>        : ohci_hcd
<tt>fdffe000-fdffefff </tt>        : ATI Technologies Inc SB600 USB 
<tt>  fdffe000-fdffefff </tt>        : ohci_hcd
<tt>fdfff000-fdfff3ff </tt>        : ATI Technologies Inc SB600 Non-Raid-5 SATA 
<tt>  fdfff000-fdfff3ff </tt>        : ahci
<tt>fec00000-ffffffff </tt>        : reserved
<tt>  fec00000-fec00fff </tt>        : IOAPIC 0
<tt>  fed00000-fed003ff </tt>        : HPET 0
<tt>    fed00000-fed003ff </tt>        : ATI Technologies Inc SBx00 SMBus Controller 
<tt>  fee00000-fee00fff </tt>        : Local APIC
<tt>    fee00000-fee00fff </tt>        : pnp 00:0e
<tt>  fff80000-fffeffff </tt>        : pnp 00:0e
<tt>  ffff0000-ffffffff </tt>        : pnp 00:0e
<tt>100000000-16fffffff </tt>        : System RAM
-DMA-
<tt> 2</tt>        : floppy
<tt> 4</tt>        : cascade

Network
*******


Interfaces
----------

-Network Interfaces-
lo    0.01MiB    0.01MiB    127.0.0.1    
eth0    0.00MiB    0.00MiB        
wlan0    6.98MiB    1.63MiB    192.168.1.109    
vboxnet0    0.00MiB    0.00MiB        

IP Connections
--------------

-Connections-
0.0.0.0:54709        0.0.0.0:*    udp    
127.0.0.1:631    LISTEN    0.0.0.0:*    tcp    
192.168.1.109:57471    ESTABLISHED    62.143.29.130:49650    tcp    
192.168.1.109:39289    ESTABLISHED    205.188.248.130:5190    tcp    
192.168.1.109:49470    ESTABLISHED    95.155.213.92:61412    tcp    
192.168.1.109:36755    ESTABLISHED    64.12.200.243:5190    tcp    
192.168.1.109:50312    ESTABLISHED    64.12.26.241:5190    tcp    
192.168.1.109:45475    ESTABLISHED    65.54.48.169:1863    tcp    
192.168.1.109:39306    ESTABLISHED    95.155.215.248:16022    tcp    
192.168.1.109:46090    ESTABLISHED    95.140.208.99:63516    tcp    
192.168.1.109:60454    ESTABLISHED    91.54.216.91:39465    tcp    
::1:631    LISTEN    :::*    tcp6    
0.0.0.0:5353        0.0.0.0:*    udp    
0.0.0.0:34943        0.0.0.0:*    udp    
127.0.0.1:50865        0.0.0.0:*    udp    
0.0.0.0:54709        0.0.0.0:*    udp    
0.0.0.0:68        0.0.0.0:*    udp    

Routing Table
-------------

-IP routing table-
192.168.1.0 / 0.0.0.0    255.255.255.0    U    wlan0    
169.254.0.0 / 0.0.0.0    255.255.0.0    U    wlan0    
0.0.0.0 / 192.168.1.1    0.0.0.0    UG    wlan0    

ARP Table
---------

-ARP Table-
192.168.1.1    00:18:39:77:0d:6e    wlan0    

DNS Servers
-----------

-Name servers-
83.169.185.33
83.169.185.97

Statistics
----------

-IP-
52182        : Total packets received
1        : With invalid addresses
0        : Incoming packets discarded
0        : Incoming packets discarded
52181        : Incoming packets delivered
24546        : Requests sent out
-ICMP-
1        : ICMP messages received
0        : ICMP messages failed
0        : ICMP messages failed
0        : ICMP messages failed
-ICMPMSG-
-TCP-
76        : Active connections openings
0        : Bad segments received.
5        : Resets sent
3        : Connection resets received
9        : Connections established
1976        : Segments received
1957        : Segments send out
30        : Segments retransmited
0        : Bad segments received.
5        : Resets sent
-UDP-
50208        : Packets received
0        : Packet receive errors
0        : Packet receive errors
22561        : Packets sent
-UDPLITE-
-TCPEXT-
8        : TCP sockets finished time wait in fast timer
157        : Delayed acks sent
854        : Packet headers predicted
316        : Acknowledgments not containing data payload received
146        : Predicted acknowledgments
3        : Congestion windows recovered without slow start after partial ack
15        : Other TCP timeouts
-IPEXT-

Shared Directories
------------------

-SAMBA-
-NFS-

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>    1200 MHz    19.515    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    

CPU CryptoHash
--------------

-CPU Cryptohash-
<big><b>This Machine</b></big>    1200 MHz    66.902    

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>    1200 MHz    7.718    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>    1200 MHz    17.722    

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>    1200 MHz    10.020    

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>    1200 MHz    15.972    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647    
```I hope someone can help me,
Regards.

Edit: looking at it again i noticed that the debug and the kern log have the same content

---

### Post by Zoot7 on 2009-12-12
Lock ups are normally caused by faulty RAM. Running memtest would be something I'd try to investigate.

---

### Post by randomguy1 on 2009-12-28
I ran Memtest serveral times now but without any errors. And i recently bought a new mainboard and my problem still exists.
One update at the bug though: When there is a sound playing when the freeze happens the last second of it is repeated over and over again. I simply didnt have one playing so i didnt notice before.
Im running Ram from too diffrent brands, 2x 512mb and 2x 2gb, but with the same clocking. Might that be a problem?
The logs i posted seem to not belong to the problem since they only appeared that one time. Is there a way i can record  what's causing the failure when it happens?

Regards

---

### Post by Zoot7 on 2009-12-28
> **randomguy1 said:**
> I ran Memtest serveral times now but without any errors. And i recently bought a new mainboard and my problem still exists.
One update at the bug though: When there is a sound playing when the freeze happens the last second of it is repeated over and over again. I simply didnt have one playing so i didnt notice before.
Im running Ram from too diffrent brands, 2x 512mb and 2x 2gb, but with the same clocking. Might that be a problem?
As long as you've them inserted and paired in the appropriate slots then there shouldn't be a problem really.

Maybe it might be worth trying a reinstall or an older version such as Jaunty just to see if the problem exists there aswell?

---

### Post by warfacegod on 2009-12-28
> 
Lock ups are normally caused by faulty RAM. Running memtest would be something I'd try to investigate.

Overheating could also be the culprit here.

---

### Post by randomguy1 on 2009-12-28
If Jaunty=ubuntu 9.04 then I've already tried that, same problem.
I doubt it's overheating because the lock-ups also appear when performing simple tasks such as watching youtube videos or simply running pidgin + my system is pretty well aired.
Can the freezes maybe be caused by ndiswrapper? Im useing it to run my fritz!box wlan-stick.

---

