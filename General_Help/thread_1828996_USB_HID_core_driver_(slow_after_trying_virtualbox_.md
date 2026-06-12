---
title: "USB HID core driver (slow after trying virtualbox 4)"
date: 2011-08-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-20
using 10.04.3
i have removed virtualbox 4 and return 3.1.6 it seems to have added ~5 seconds to my boot time (at least at the ubuntui plymouth splash screen) and i had it down to ~9 seconds before as a perfectionist it is getting under my nerves
my guess it it left something to enable usb support in virtualbox
here is part of my dmesg
```
[    3.712963] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    3.714460] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    3.719702] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    3.722055] usbcore: registered new interface driver hiddev
[    3.726085] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input3
[    3.726143] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:13.0-2/input0
[    3.726155] usbcore: registered new interface driver usbhid
**[COLOR=Red][    3.726156] usbhid: USB HID core driver[/COLOR]**
[    8.496371] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.712343] Adding 16779888k swap on /dev/sdb4.  Priority:-1 extents:1 across:16779888k 
[    8.788889] udev: starting version 151
[    8.820842] WARNING! power/level is deprecated; use power/control instead
[    8.867237] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [irq 2816-2831 64bit pref window]
[    8.867240] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.868274] lp: driver loaded but no devices found
[    8.870042] EDAC MC: Ver: 2.1.0 Jan 25 2011
```i have older dmesg output here
[http://ubuntuforums.org/showthread.php?t=1773230](http://ubuntuforums.org/showthread.php?t=1773230)
-------------------------------------------------------------------------------------
edit
notice the 1st udevd and wait for root
old boot chart
[s][http://i.imgur.com/FaAPl.png](http://i.imgur.com/FaAPl.png)[/s] [http://i.imgur.com/gHM6Z.png](http://i.imgur.com/gHM6Z.png)
new boot chart
[http://i.imgur.com/ySVIv.png](http://i.imgur.com/ySVIv.png)
could this be cause of the xul runner update i got earlier?
**-------------------------------------------------------------------------------------**
[SIZE=4][FONT=Arial Black]Since the Title is screwed up on this i made a new [thread]("http://ubuntuforums.org/showthread.php?t=1829736")[/FONT][/SIZE] PS it is now solved

---

### Post by pqwoerituytrueiwoq on 2011-08-20
What the...
wrongs dam chart this should be the old one [http://i.imgur.com/gHM6Z.png](http://i.imgur.com/gHM6Z.png)
if you notice udevd at the top only takes about 3 times longer in the more recent one
i have a backup if someone can tell me what files i need to compare i have found removed all the just left over from vb 4 (startup and shutdown scripts)

---

### Post by pqwoerituytrueiwoq on 2011-08-20
every time i think about the boot time it ticks me off that it got longer over some pointless delay i can't undo sorry this post is under 24 hrs i stayed up till 4 am looking for a fix and scowering the system for clues

---

