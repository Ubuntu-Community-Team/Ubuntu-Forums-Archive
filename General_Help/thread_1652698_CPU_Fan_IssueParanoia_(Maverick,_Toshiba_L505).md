---
title: "CPU Fan Issue/Paranoia (Maverick, Toshiba L505)"
date: 2010-12-25
forum: General Help
---

### Post by R0nald on 2010-12-25
I am having difficulty setting up lm-sensors so that I can monitor fan speed and temps. I have been following the[How-To]("http://ubuntuforums.org/showthread.php?t=2780") on the forums, but it appears I don't have the sensors detected/loaded properly.

This is the current output:
```
ronald@ronald-Satellite-L505:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +69.0°C  (crit = +114.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +63.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +57.0°C  (high = +105.0°C, crit = +105.0°C) 
```

Below is a copy of what I have been trying in terminal. Any help would be greatly appreciated!

Here is a walkthrough of sensors-detect:
```
ronald@ronald-Satellite-L505:~$ sudo sensors-detect
[sudo] password for ronald: 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: TOSHIBA Satellite L505 (laptop)
# Board: TOSHIBA Portable PC

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
[COLOR="Red"][B]Intel Core family thermal sensor...                         Success!
    (driver `coretemp')[/B][/COLOR]
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
[COLOR="red"][B]Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11[/B][/COLOR]
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
[COLOR="Red"][B]Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9[/B][/COLOR]

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
[COLOR="red"][B]Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)[/B][/COLOR]

Next adapter: DPDDC-D (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus I801 adapter at 5000 (i2c-3)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
[COLOR="red"][B]Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)[/B][/COLOR]
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
[COLOR="red"][B]Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)[/B][/COLOR]

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
```

And the sensors-detect step ends with this:
```
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)Y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.
```

Any ideas about what further steps I can take to get lm-sensors working correctly?

Possibly necessary info:
10.10 64-bit
Intel T4300 dual core
Western Digital WD3200BEKT HDD

---

### Post by R0nald on 2010-12-25
Also, how rude of me!
Happy holidays and a very Merry Christmas to all!

---

### Post by R0nald on 2010-12-26
Bump for a big edit in first post. 

If someone could look through the the terminal logs to help this poor n00b, that would be fantastic.:D

---

