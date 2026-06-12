---
title: "lm_sensors not reporting fan speed"
date: 2012-06-13
forum: General Help
---

### Post by kevbelisle on 2012-06-13
Hi,

I've spent the last few hours trying to get this to work and haven't found anything...

I'm running an Intel G530 on a Gigabyte H61M-S2H motherboard. I think I'm running GRUB2 if that changes anything (I don't have a menu.lst, I have a grub.cfg)

Here's what "sensors" outputs :
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +43.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +43.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +40.0°C  (high = +82.0°C, crit = +102.0°C)

```

I'm thinking it might have to do with this output from "sensors-detect" :
```
Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)
[...]
Note: there is no driver for ITE IT8728F Super IO Sensors yet.
Check http://www.lm-sensors.org/wiki/Devices for updates.

```

According to [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) :
> 
Support was added to the it87 driver, considering the IT8728F as fully compatible with the IT87281F. Please report if you think the driver is misbehaving.


I tried adding "it87" with "coretemp" to /etc/modules and rebooted but nothing changed...
Do I need to install this driver somehow?

I tried the "acpi_enforce_resources=lax" trick from here: [http://hydra.geht.net/tino/howto/linux/fixes/w83627hf/](http://hydra.geht.net/tino/howto/linux/fixes/w83627hf/)
But that didn't work...
This same fix is mentioned here: [https://wiki.archlinux.org/index.php/Lm_sensors](https://wiki.archlinux.org/index.php/Lm_sensors)



Here's what "sudo sensors-detect" outputs :
```
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Gigabyte Technology Co., Ltd. H61M-S2H

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8728F Super IO Sensors'                        Success!
    (address 0x290, driver `to-be-written')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): 

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus disabled (i2c-0)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 gmbus ssc (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 GPIOB (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 gmbus vga (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 GPIOA (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 gmbus panel (i2c-5)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 GPIOC (i2c-6)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 gmbus dpc (i2c-7)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 GPIOD (i2c-8)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 gmbus dpb (i2c-9)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 GPIOE (i2c-10)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 gmbus reserved (i2c-11)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95245'...             No
Probing for `National Semiconductor LM64'...                No
Probing for `SMSC EMC1047'...                               No
Probing for `SMSC EMC1402'...                               No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x58
Probing for `Analog Devices ADT7462'...                     No
Probing for `Andigilog aSC7512'...                          No
Client found at address 0x5c
Probing for `Analog Devices ADT7462'...                     No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Client found at address 0x73
Probing for `FSC Poseidon I'...                             No
Probing for `FSC Poseidon II'...                            No
Probing for `FSC Scylla'...                                 No
Probing for `FSC Hermes'...                                 No
Probing for `FSC Heimdal'...                                No
Probing for `FSC Heracles'...                               No
Probing for `FSC Hades'...                                  No
Probing for `FSC Syleus'...                                 No

Next adapter: i915 gmbus dpd (i2c-12)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: i915 GPIOF (i2c-13)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: DPDDC-B (i2c-14)
Do you want to scan it? (YES/no/selectively): 

Next adapter: DPDDC-C (i2c-15)
Do you want to scan it? (YES/no/selectively): 

Next adapter: DPDDC-D (i2c-16)
Do you want to scan it? (YES/no/selectively): 

Next adapter: SMBus I801 adapter at 0500 (i2c-17)
Do you want to scan it? (yes/NO/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Note: there is no driver for ITE IT8728F Super IO Sensors yet.
Check http://www.lm-sensors.org/wiki/Devices for updates.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

```

---

### Post by habana on 2012-06-13
My Gigabyte board uses the same chip. You will note from your first link that the chip is supported in kernel 3.3 so we may have to wait for that. There is a standalone driver which I tried to install but failed miserably:p

If anybody knows how to do that properly, I would be grateful for advice.

---

### Post by kevbelisle on 2012-06-13
I gather that Ubuntu 12.10 will release in october and include linux kernel 3.4, unless my Google-fu has failed me...

What did you do to attempt to install the driver?

Copy the make file and the it87.c files into a directory and issu a "sudo make install" command?

This might help us: [http://mhvlug.org/pipermail/mhvlug/2011-February/031086.html](http://mhvlug.org/pipermail/mhvlug/2011-February/031086.html)
And, a couple messages later there's a link to this: [https://bugzilla.redhat.com/show_bug.cgi?id=497670](https://bugzilla.redhat.com/show_bug.cgi?id=497670)

I'm going to try this tonight!

---

### Post by habana on 2012-06-13
That's exactly what I did and the object code files are sitting in the directory I created. Nothing else happened. I hope you have more luck!

---

### Post by ratcheer on 2012-06-13
I had exactly the same experience, two days ago. Install the latest version of it87 and it works. I got mine from a different site, but I am pretty sure it is the same stuff.

[http://khali.linux-fr.org/devel/misc/it87/](http://khali.linux-fr.org/devel/misc/it87/)

There is some explanation on this page:

[http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

Tim

---

### Post by kevbelisle on 2012-06-13
Ok, test in progress.
Here's my step-by-step*...

[LIST=1]
[*]Downloaded "Makefile" and "it87.c" files into a folder on my desktop
[*]From terminal in said folder, ran "sudo make" and "sudo make install"
[*]Reboot
[*]From terminal, ran "sudo sensors-detect"
[*]Good signs :
```
Trying family `ITE'...                               Yes
Found `ITE IT8728F Super IO Sensors'                 Success!
(address 0x290, driver `to-be-written')
```
[*]Epic win :
```
kevin@HTPC:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +32.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +31.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +31.0°C  (high = +82.0°C, crit = +102.0°C)

it8728-isa-0290
Adapter: ISA adapter
in0:          +1.04 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +0.07 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +3.01 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.98 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +0.01 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +0.74 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +1.51 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.38 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.17 V  
fan1:        1173 RPM  (min =    0 RPM)
fan2:        1433 RPM  (min =    0 RPM)
temp1:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +21.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
intrusion0:  ALARM

```
[/LIST]

**habana**, I hope you can get this to work!!
I'm running an up-to-date version of Ubuntu 12.04, nothing special really... Install is only 1 or 2 weeks old.

*Before all this, I had added "coretemp" and "it87" to /etc/modules. Here's my /etc/modules :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
coretemp
it87
```

---

### Post by habana on 2012-06-14
kevbelisle you're a star! All I had to do was to add it87 to the etc/modules file and the job was done:p

Thanks very much for sorting this out and have a great day!

---

### Post by kevbelisle on 2012-06-17
I installed updates to Ubuntu yesterday and had to re-make+install the it87 driver for some reason...

---

### Post by habana on 2012-06-18
All still OK here and I have all updates installed too.

---

### Post by habana on 2012-06-28
I've now discovered that make install has to be run again after a kernel upgrade

---

### Post by ratcheer on 2012-06-28
> **habana said:**
> I've now discovered that make install has to be run again after a kernel upgrade

Sure.

Tim

---

### Post by Corvair on 2012-09-10
kevbelisle


I have the same problem, using XSensors, I don't see the fan speeds.
Your solution seems to work.
I don't understand how to download the  "Makefile" and "it87.c" files or where you download them from.
Can you help me on this As I am not a specialist on this?

---

### Post by ratcheer on 2012-09-10
@corvair: Here is the page to find it on: [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) Look for Manufacturer ITE in the leftmost column.

There are several choices. I used the one that says it is for my Z68 motherboard. [http://khali.linux-fr.org/devel/misc/it87/](http://khali.linux-fr.org/devel/misc/it87/) Yours may or may not be the same.

Good luck,
Tim

---

### Post by dphurst on 2013-01-12
[FONT="Georgia"][SIZE="3"]I've updated the kernel in 12.04 using the backported quantal 3.5 kernel.  It has the IT87 updated chipset driver.  By doing this, there is no need to make the driver for the kernel and updates won't break a manually installed driver.

After inserting the driver with modprobe:

sudo modprobe it87

sensors will report not only the coretemp module's temperatures but will give fan speeds and additional temperatures from the it87 module.  The configuration of the temperatures seems okay for the first and third values.  The second value is -55 Centigrade, so that is a bit bogus.  A correct configuration for the chipset would be nice, but I don't have that.  Here is the output that sensors provides once both modules are inserted into the kernel.  Also, this is the 3.3.1 version of lm-sensors from the repositories for 12.04 that I'm using.[/SIZE][/FONT]

[FONT="Courier New"][SIZE="2"]coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +52.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +45.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +52.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +52.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +50.0°C  (high = +80.0°C, crit = +98.0°C)

it8728-isa-0290
Adapter: ISA adapter
in0:          +1.04 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +2.04 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.94 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.95 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.23 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +1.20 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +1.52 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.36 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.26 V  
fan1:        2122 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:         798 RPM  (min =   10 RPM)
temp1:        +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        -55.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +41.0°C  (low  = +127.0°C, high = +80.0°C)  sensor = thermistor
intrusion0:  OK[/SIZE][/FONT]

---

