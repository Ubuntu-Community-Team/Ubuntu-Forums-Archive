---
title: "Problems loading k71882fg sensors module"
date: 2010-06-06
forum: General Help
---

### Post by geoffjay on 2010-06-06
I've done the usual for installing lm-sensors and ran the mkdev.sh script that can be found all over the internet if one searches for "ubuntu lm-sensors" then I run sensors-detect answering yes to all questions and get (just the highlights):

============================

# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: MSI MS-7612
# Board: MSI NF980-G65 (MS-7612)

...
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
...
Found `Fintek F71889FG Super IO Sensors'                    Success!
    (address 0xa00, driver `f71882fg')
...
Using driver `i2c-nforce2' for device 0000:00:01.1: nVidia Corporation nForce SMBus (MCP78S)
Module i2c-dev loaded successfully.
...
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
...
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
...
Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Driver `f71882fg':
  * ISA bus, address 0xa00
    Chip `Fintek F71889FG Super IO Sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
f71882fg
#----cut here----

============================

Normally after that I would try to modprobe the module but when I did that I got:

$ sudo modprobe f71882fg
FATAL: Error inserting f71882fg (/lib/modules/2.6.32-22-generic/kernel/drivers/hwmon/f71882fg.ko): No such device

The site [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) shows that the f71882fg hardware has been part of the kernel since 2.6.24 and I'm on 2.6.32, also if I `locate f71882fg.ko` I get:
/lib/modules/2.6.32-21-generic/kernel/drivers/hwmon/f71882fg.ko
/lib/modules/2.6.32-22-generic/kernel/drivers/hwmon/f71882fg.ko

I found various forum posts that say to add the kernel option "acpi_enforce_resources=lax" and restart (after of course running update-grub) but that didn't help.

In case it matters 
$ uname -a
Linux studio 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

If anyone can shed a little light on this I would greatly appreciate it, I just bought a new mobo/CPU and would like to OC but I'm not keen on doing that until I can monitor the core temp.

Thanks.

---

### Post by geoffjay on 2010-06-07
No one has installed this hardware before???

---

### Post by geoffjay on 2010-06-11
If anyone happens to read this because they are having the same problem I was able to get both the k10temp and f71882fg modules working for this mobo by compiling kernel 2.6.35-2 following the instructions at: [http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/)

cheers.

---

### Post by ternyk on 2010-07-11
I had the same problem on my mobo MSI 785GM-E51 but didn't want to install a new kernel. I solved it by downloading updated f71882fg module from [http://khali.linux-fr.org/devel/misc/f71882fg/](http://khali.linux-fr.org/devel/misc/f71882fg/). It works very well.
Also remember that for 2.6.32 kernel you should also compile k10temp module.

---

### Post by geoffjay on 2010-07-11
I had actually tried that but somewhere along the way botched something and it didn't work. Any chance you'd be able to put the steps you used to add this module?

---

### Post by keteflips on 2010-08-20
Same error here :popcorn:

---

