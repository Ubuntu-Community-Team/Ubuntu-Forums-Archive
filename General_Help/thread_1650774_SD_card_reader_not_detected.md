---
title: "SD card reader not detected"
date: 2010-12-22
forum: General Help
---

### Post by satish.kalkur on 2010-12-22
Hello Developers,

I inserted a Card Reader into my Lenovo Thinkpas T400 and inserted a 4gb card inside it.
It didn mount automatically and when i tried to mount it manually I got an error message stating as follows:

''Error mounting: mount: block device /dev/sdb1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so''

Then i tried dmesg | tail
''[   26.238009]   groups: 1 0
[   28.977263] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.213978] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input13
[   34.720515] eth0: no IPv6 routers present
[   34.992711] EXT3-fs: INFO: recovery required on readonly filesystem.
[   34.992714] EXT3-fs: write access unavailable, cannot proceed.
[   70.706725] EXT3-fs: INFO: recovery required on readonly filesystem.
[   70.706729] EXT3-fs: write access unavailable, cannot proceed.
[ 1227.444122] EXT3-fs: INFO: recovery required on readonly filesystem.
[ 1227.444126] EXT3-fs: write access unavailable, cannot proceed.''

I also tried several commands to see if my usb is detected or not that is ''lsusb''
''Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 001 Device 002: ID 04b3:4485 IBM Corp. Serial Converter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub''

Alcor Micro is the card reader

This SD card is from freescale and it has data related to imx51 processor.so its quite important for my development

How do get to acces it..?
I even visited other posts related to this but no use

Thanks

---

### Post by jajjax on 2011-10-29
Have you got this problem solved ? 
I have the same problem that you describes.:confused:

---

### Post by linuxwin2 on 2011-10-29
What's the filesysem of your SD card?
 
Can you remove the card the open a terminal and put
[code0$ sudo tail-f /var/log/message[/code]
Then insert the SD card and put the ouput
]

---

### Post by ofnuts on 2011-10-29
> **jajjax said:**
> Have you got this problem solved ? 
I have the same problem that you describes.:confused:
Try another card with the same reader or the same card in another reader. And remember that the 4GB cards are on the frontier between SD and SDHC so you can get them of both types (the plain SD version isn't really standard-compliant). The SDHC ones won't be read by SD-only card readers (ie, ancient ones). Support the SD ones is never guaranteed.

---

