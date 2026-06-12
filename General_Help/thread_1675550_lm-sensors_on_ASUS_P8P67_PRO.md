---
title: "lm-sensors on ASUS P8P67 PRO"
date: 2011-01-25
forum: General Help
---

### Post by deathbysushi on 2011-01-25
Hello all! I just set up a new machine with a Core i5-2500k and a ASUS P8P67 motherboard. I am trying to get conky working but none of my sensors are being detected. When running lm-sensors, I get the following output:

```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: System manufacturer System Product Name
# Board: ASUSTeK Computer INC. P8P67 PRO

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc333
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
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
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Found unknown SMBus adapter 8086:1c22 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 


Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 
Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 


Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 
Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 


Next adapter: NVIDIA i2c adapter  (i2c-6)
Do you want to scan it? (YES/no/selectively): Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 
No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-7)
Do you want to scan it? (YES/no/selectively): 
Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

Do you happen to know how I can fix this or will I probably have to wait for an update since my motherboard is new? 

Thank you so much!

---

### Post by khamil8686 on 2011-01-25
maybe the lm-sensors tarball from the project webpage supports your sensors, the repo's version seems to be out of date (i installed the repo's lm-sensors and have version 3.1.2 on my machine. im not sure which version you have but run ```
sensors -v
``` in a terminal and it will tell you. the new version available is 3.2.0 and you can download the tarball from
[http://lm-sensors.org/wiki/Download]("http://lm-sensors.org/wiki/Download")
uninstall the repo version of lm-sensors and then extract the tarball to a directory, read the readme and the install file in the tarball to learn to install 3.2 manually and then run ```
sudo sensors-detect
```
again and see if it detects your sensors :) hope this helps!

---

### Post by Frogs Hair on 2011-01-25
If the above solution doesn't work answer yes to all questions  and try ```
sensors
```

---

### Post by deathbysushi on 2011-01-25
Thanks for the help but, unfortunately, no luck. I ran 3.2.0 and it still gives me the same output (see below):

```
sudo sensors-detect 
# sensors-detect revision 5861 (2010-09-21 17:21:05 +0200)
# System: System manufacturer System Product Name
# Board: ASUSTeK Computer INC. P8P67 PRO

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc333
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
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
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-6)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-7)
Do you want to scan it? (YES/no/selectively): 

Next adapter: SMBus I801 adapter at f000 (i2c-8)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
marzec@triton:~/lm_sensors-3.2.0$ cd
marzec@triton:~$ sudo sensors-detect 
# sensors-detect revision 5861 (2010-09-21 17:21:05 +0200)
# System: System manufacturer System Product Name
# Board: ASUSTeK Computer INC. P8P67 PRO

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc333
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
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
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-6)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-7)
Do you want to scan it? (YES/no/selectively): 

Next adapter: SMBus I801 adapter at f000 (i2c-8)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

Any ideas on what I can do?

---

### Post by khamil8686 on 2011-01-25
you could google "*your motherboard model num* thermal sensor" and see
if you can find the names of the thermal sensors on your motherboard and see if they are supported on the
lm-sensors website, if the drivers arent there yet then im afraid youre out of luck :( you could
possibly see if there is a PCI card with a thermal sensor on it with a supported driver 
until the drivers are supported

---

### Post by psusi on 2011-01-25
I'm struggling with the same problem.  I have emailed Asus about it, we will see what they say.

---

### Post by deathbysushi on 2011-01-26
> **psusi said:**
> I'm struggling with the same problem.  I have emailed Asus about it, we will see what they say.

Great! Please keep me posted :D

Thanks again to everyone for your help. I am patient so I can wait on this, but it would be cool to have!

---

### Post by psusi on 2011-01-26
I am in contact with Asus about the deficiencies of their bios ACPI support that prevent this from just working out of the box.  I have also learned that they use the NCT6776F chip, which does not yet have a kernel driver.  I have obtained the data sheet for the chip and hopefully will be writing a driver for it soon.

I am also toying with the idea of patching the ACPI tables so they work right.  We will see if Asus will do this for us or not.

The other defect I have found is that the ACPI P-state frequency table is given incorrect frequencies when overclocking.  The auto OC feature increased my BCLK to 103 MHz, which puts the CPU clock speed at 3,399 MHz, but the P-state table shows it going up to 5,800 MHz.

---

### Post by jpn2605 on 2011-01-28
Hello,

I intend to buy a motherboard Asus " P8P67 PRO", but I wonder about its compatibility with Ubuntu.

Except lm-sensors problem, did you experienced any other problem installing Ubuntu on your P8P67 PRO motherboard ?  Specially : sound output, mouse, keyboard and USB ports inputs, hard drive access, ...

What Ubuntu release did you experienced ?  (10.10, Kubuntu ?)
Thank you for sharing your experience !

---

### Post by psusi on 2011-01-28
Just that suspend problem with the USB3.  Hell, even the bluetooth works.  This is with 10.10.

---

### Post by ian dobson on 2011-01-29
Hi,

OK, there's not support for the nct6776f in hwmon/lm-sensors projects, so I decided to have a go at writing my own.

And here are the results:-

```

n6776f-isa-0290
Adapter: ISA adapter
CPU voltage: +1.17 V  (min =  +1.00 V, max =  +1.20 V)
AVCC:        +3.36 V  (min =  +0.00 V, max =  +0.00 V)
3VCC:        +3.34 V  (min =  +0.00 V, max =  +0.00 V)
3VSB:        +3.42 V  (min =  +0.00 V, max =  +0.00 V)
Unknown:     +3.28 V  (min =  +0.00 V, max =  +0.00 V)
RAM:         +1.54 V  (min =  +2.04 V, max =  +2.04 V)
Case Fan:    503 RPM  (min =  120 RPM)
CPU Fan:     954 RPM  (min =  500 RPM)
HD FAN:      164 RPM  (min =  100 RPM)
Unknown:     630 RPM  (min =  400 RPM)
Sys Temp:    +19.0Â°C  (high = +35.0Â°C, hyst = +37.0Â°C)  sensor = thermistor
CPU Temp:    +34.5Â°C  (high = +40.0Â°C, hyst = +45.0Â°C)  sensor = thermistor

```

The fan speeds are read directly from the chips registers (rather than time between pulses and the fan divider), voltages appear to be correct, I just need to work out the calculation factors, temperatures are almost the same as in the BIOS.

What doesn't work is alarming for the fans due to the chip not supporting it, and I'm not a good enough kernel programmer to workout how to use the internal data structures of the driver for alarming.

Once the code has had a chance to dry abit I'll send it to the lm-sensors devs.

Other than that the motherboard seems to work well under linux. The only problem I've seen is the compatibility with some 4 pin fans, but that's a BIOS problem more than anything to do with Linux.


Regards
Ian Dobson

---

### Post by deathbysushi on 2011-01-29
This is awesome work! Thank you again for taking a look into this!

---

### Post by psusi on 2011-01-30
I have had a thread going on the lm-sensors list for the last few days.  Jean Delvare added detection support for the chip to sensors-detect, and suggested that I modify the w83627ehf driver to support this chip as well, since they seem very similar, which I was just starting to do.

Did you write this from scratch and would you mind sharing it now?

---

### Post by ian dobson on 2011-01-30
> **psusi said:**
> I have had a thread going on the lm-sensors list for the last few days.  Jean Delvare added detection support for the chip to sensors-detect, and suggested that I modify the w83627ehf driver to support this chip as well, since they seem very similar, which I was just starting to do.

Did you write this from scratch and would you mind sharing it now?

I just took the w83627ehf module and modified the registers for the fan reading,alarming etc. I still need to check the the voltage reading is correct.

I actually read the RPM directly from the chip rather than reading the counter/divider and calculating the RPM.

I've already mailed Jean Delvare and he doesn't have any time to look at this at the moment, so I post the code to the lm-sensors list when I'm happy with it.

Regards
Ian Dobson

---

### Post by psusi on 2011-01-30
Cool.  Did you fork it into a separate driver, or just add the new chip id and characteristics to the existing driver?  I'll keep an eye out and give it a once over when you post it.

---

### Post by ian dobson on 2011-01-30
Hi,

I've created a new driver based on the w83627ehf and just changed the bits that were different. I looked at just extending the ehf driver but it started getting really messy.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-02-27
Hi,

OK the standard w83627ehf driver now has support for the nct6776f and nct6775f. Guenter Roeck has sent a pull request to Linus so the code should make it into kernel .38

Regards
Ian Dobson

---

### Post by ian dobson on 2011-03-07
Ok,

We missed the .38 merge window, maybe we can get the driver into .39. I have a standalone driver with patchs for fan signal debouncing that I'd like to get tested, if anyone has aboard with a nct6776f or nct6775f superIO chip and would like to test the driver, please let me know.

Regards
Ian Dobson

---

### Post by yeeeev on 2011-03-17
I'd be happy to test your patch (and try to get quieter CPU fans :) ).
Can you please post it, or send it to me: yoav AT yoav DOT ws

Thanks,
Yoav
----------------
blog.yoav.ws

---

### Post by ian dobson on 2011-03-17
> **yeeeev said:**
> I'd be happy to test your patch (and try to get quieter CPU fans :) ).
Can you please post it, or send it to me: yoav AT yoav DOT ws

Thanks,
Yoav
----------------
blog.yoav.ws

You can download the source from  [http://mail.planet-ian.com/w83627ehf](http://mail.planet-ian.com/w83627ehf)

to compile/install just type
make
make install
modprobe w83627ehf

Then type sensors to see what it found.

We already have enough testers for the normal nct6776f chip, if you have a nct6775f I'd be interested in the results.

Regards
Ian Dobson

---

### Post by paulisdead on 2011-03-19
Did you forget to put the URL in?  I just got my p8p67 deluxe up and running, and would like to have a go as well.

---

### Post by ian dobson on 2011-03-19
> **paulisdead said:**
> Did you forget to put the URL in?  I just got my p8p67 deluxe up and running, and would like to have a go as well.

added

Regards
Ian dobson

---

### Post by klotz on 2011-03-21
I have a P8P67 with the new R3 chipset and just tried this.
Once I removed the modprobe options I had in /etc/modules.conf for the previous workaround (pkgtemp, coretemp, w83627ehf force_id=0x8860) then ran sensors-detect and sensors I now get fan2 as CPU fan.

I look forward to seeing this in the released kernels.

---

### Post by ian dobson on 2011-03-22
> **klotz said:**
> I have a P8P67 with the new R3 chipset and just tried this.
Once I removed the modprobe options I had in /etc/modules.conf for the previous workaround (pkgtemp, coretemp, w83627ehf force_id=0x8860) then ran sensors-detect and sensors I now get fan2 as CPU fan.

I look forward to seeing this in the released kernels.

Me to, it's a pain recompiling/installing the module everytime I update the kernel. It's not that it takes long, it's another thing that can be forgotten.

The module/patch should make it into the .39 merge window, so we'll see it in Ubuntu 11.10 I'd imagine, unless the ubuntu team backport it into earlier kernels. That would be nice but who knows.

Regards
Ian Dobson

---

### Post by JoelOl75 on 2011-03-22
Maybe it can be automated for now with dkms

I don't have that hardware but would a

wget [http://mail.planet-ian.com/w83627ehf](http://mail.planet-ian.com/w83627ehf)

Then use checkinstall to build a deb pkg and install it then

sudo dkms add -m w83627ehf
sudo dkms build -m w83627ehf
sudo dkms install -m w83627ehf

Not sure if this will work but I know there's a way to get the source added to dkms so new kerrnel updates will auto rebuild the module but I think the source needs to be debianized first.  If checkinstall wont do it maybe the devscripts pkg can.

---

### Post by klotz on 2011-03-23
With my Rev 3 board and the new 1305 BIOS that came with it, I no longer get OC speeds.  The BIOS OC Tuner claims it's doing it, and even if I do cpufreq-set --cpu 0 --max 4.70GHz (etc) I still get 3.55 GHz as the max speed reported by Len Brown's turbostat program.  

Also, some compile task benchmarks I've been using are slow, right in line with no OC benefit.  (Was 20-21s, now 28s.)

I don't know if it's the BIOS change or a kernel issue, or some other thing.  Too many things changed at once.

---

### Post by ian dobson on 2011-03-23
> **klotz said:**
> With my Rev 3 board and the new 1305 BIOS that came with it, I no longer get OC speeds.  The BIOS OC Tuner claims it's doing it, and even if I do cpufreq-set --cpu 0 --max 4.70GHz (etc) I still get 3.55 GHz as the max speed reported by Len Brown's turbostat program.  

Also, some compile task benchmarks I've been using are slow, right in line with no OC benefit.  (Was 20-21s, now 28s.)

I don't know if it's the BIOS change or a kernel issue, or some other thing.  Too many things changed at once.

Woe, you already have a rev3 board, mine should be comming in afew weeks.

I take it you've been through the reset bios to default/optimised defaults then reconfigure.

Regards
Ian Dobson

---

### Post by klotz on 2011-03-23
> **ian dobson said:**
> Woe, you already have a rev3 board, mine should be comming in afew weeks.

I take it you've been through the reset bios to default/optimised defaults then reconfigure.

Regards
Ian Dobson

Thanks!  Yes, I got it a few days ago and had to wait until I had time to do the switch.  Then it took a day or two to establish that the OC settings in the BIOS weren't having an effect.

Yes, the BIOS part goes swimmingly.  It finds the same OC points (43/103) as before.  But it has no effect after boot.  Once I managed to get it to run faster, but I can't reproduce it.  Both the turbostat program and my own benchmarks show it.

Last night I enabled the idle states but I guess I enabled too many because it was in an unwakeable sleep this morning.  I set them back to AUTO, as it's supposed to help with power consumption, not with OC.

So anyway, I don't know if it's BIOS changes or kernel changes or what, but it's just not happening.  I'll keep plugging at it.

Your w83627ehf mods do work well though and I'm able to monitor fan speed and get more realistic numbers for core temps as well now.  Thanks!

---

### Post by psusi on 2011-03-23
> **klotz said:**
> 
Last night I enabled the idle states but I guess I enabled too many because it was in an unwakeable sleep this morning.  I set them back to AUTO, as it's supposed to help with power consumption, not with OC.

By "idle states" you mean the setting to hide C3/C6?  You want those states on.  The more time at least some of the cores spend in the lower power states, the more thermal room you have for turbo boost.

---

### Post by ian dobson on 2011-03-23
> **klotz said:**
> Thanks!  Yes, I got it a few days ago and had to wait until I had time to do the switch.  Then it took a day or two to establish that the OC settings in the BIOS weren't having an effect.

Yes, the BIOS part goes swimmingly.  It finds the same OC points (43/103) as before.  But it has no effect after boot.  Once I managed to get it to run faster, but I can't reproduce it.  Both the turbostat program and my own benchmarks show it.

Last night I enabled the idle states but I guess I enabled too many because it was in an unwakeable sleep this morning.  I set them back to AUTO, as it's supposed to help with power consumption, not with OC.

So anyway, I don't know if it's BIOS changes or kernel changes or what, but it's just not happening.  I'll keep plugging at it.

Your w83627ehf mods do work well though and I'm able to monitor fan speed and get more realistic numbers for core temps as well now.  Thanks!

Just try resetting the BIOS and setting up the options again. Also have you enabled the 2 turbo switches on the motherboard?

If the CPU temperaure is too high then turboboost doesn't boost as far, so what are your temperatures like? Are you sure the thermal paste is OK?

Regards
Ian Dobson

---

### Post by paulisdead on 2011-03-24
I got the deluxe model, a b3 as well, and turbostat is reporting the overclocked speeds.  There's a firmware that came out on the 18th, I just installed.  They only list a fix for the nec usb firmware, but who knows what else they changed, since nobody really lists all the stuff they fix in these updates.  I think it found the same auto oc point as yours, 103x43 on an i7 2600k.  Do you have speedstep enabled in the firmware?  Does the speed clock down when it's idle?

The core-temp module seems to be the only way I've gotten temps out of it, but it seems accurate.  I see the cores individually at 25-30C idle, and around 55-60C under a full load in handbrake, so that seems about right.  With Ian's module I get fan speeds.

---

### Post by klotz on 2011-03-24
Thank you for all the help.

> **ian dobson said:**
> Just try resetting the BIOS and setting up the options again. Also have you enabled the 2 turbo switches on the motherboard?
Yes, I've done that a few times.  There seems to be some odd dependency.
I have the TPU and EPU on on the motherboard and haven't touched them.

> **ian dobson said:**
> 
If the CPU temperaure is too high then turboboost doesn't boost as far, so what are your temperatures like? Are you sure the thermal paste is OK?

Temps are lower now than they were before (stock heatsink, then switched to a better one with MX3 pre-applied, then for B3 board I used IC7).  It's hard to compare completely because I don't trust the temps prior to your patch, but they're well within range.  The OC speeds according to turbostat simply max out well below what the BIOS multiplier is set for.  My compile task test was 21s at 4.7GHz before, and now it's back up to the 28s range.  The one time I managed to get turbostat to report faster speeds was also the one time that the compile finished in 21s as well.

So I'm reasonably sure that turbostat gives me good numbers, and I can compare across boots and see what effect my changes have.

I'll go back and check the Cx states again as psui recommends in [http://ubuntuforums.org/showpost.php?p=10592270&postcount=29](http://ubuntuforums.org/showpost.php?p=10592270&postcount=29) and hope I get it right and it doesn't go to sleep again.

So, it's sad, but something's changed and I don't know what.

---

### Post by klotz on 2011-03-24
OK, I enabled C1E, C3, and C6 in BIOS (changed AUTO to ENABLED) and I see >3.4 GHz now with 4x burnP6 running, but it throttles back after about 20 seconds.  Temps reach 55-60C. So perhaps I have a combination of problems: idle states disabled by default in the 1304 BIOS is one, but there's another, which may be improper TIM application, or may be some other BIOS setting.

---

### Post by jpn2605 on 2011-04-15
Thanks !
Did you successfully try  a hard disk plugged on a 6 Gb/s port ?

---

### Post by jebus_beler on 2011-04-24
I'm thinking of getting this board as part of a linux system I want to build.  I've skimmed this thread and a few others and it seems that the board is relatively well supported under linux.  For all the people who have it, can you recommend it or are there features that don't seem like they'll be supported anytime soon?

From what I can tell the relevant components are:

• Intel 82579 Gigabit LAN Dual interconnect (linux supported).
• Realtek ALC892 8-Channel High Definition Audio CODEC (linux supported) 
• VIA 6308P controller supports 2 x 1394a port(s)
• Marvell® 9120 controller 
• JMicron® JMB362 SATA controller
• Bluetooth

Can anyone who has this board say if they know if any of the above do or don't work with the latest ubuntu?

thanks!

---

### Post by paulisdead on 2011-04-24
> **jebus_beler said:**
> I'm thinking of getting this board as part of a linux system I want to build.  I've skimmed this thread and a few others and it seems that the board is relatively well supported under linux.  For all the people who have it, can you recommend it or are there features that don't seem like they'll be supported anytime soon?

From what I can tell the relevant components are:

• Intel 82579 Gigabit LAN Dual interconnect (linux supported).
• Realtek ALC892 8-Channel High Definition Audio CODEC (linux supported) 
• VIA 6308P controller supports 2 x 1394a port(s)
• Marvell® 9120 controller 
• JMicron® JMB362 SATA controller
• Bluetooth

Can anyone who has this board say if they know if any of the above do or don't work with the latest ubuntu?

thanks!

I disabled the Marvell NIC and the jmicron controller, so I can't say for sure if they work, but I'd be really shocked if they didn't.  The Intel NIC and and the sound work fine for me.  The firewire at least shows up, but I don't have any firewire devices, so I haven't actually tried it.  Same with the bluetooth.  The Intel SATA ports work great, and there's 6 of them.

About the only thing that was any trouble to get working was the hardware sensors, which got covered in this thread.  

I have had a few hard lockups when using the USB 3.0 ports, but I have seen the more recent kernels had bunch of fixes for USB 3, so hopefully when 11.04 comes out that stops happening.

---

### Post by psusi on 2011-04-25
I also don't have any firewire devices, but have noticed sometimes in my kernel log complaints about an unexpected interrupt being generated by it and it shuts down I think.  Under Maverick I can't suspend unless I unload the USB3 driver, but this has been fixed in newer kernels.  I also don't have any USB3 devices to test but it at least shows up and *appears* to be working.

I managed to get the bluetooth to pair with my cell phone and transfer files but that's all I have managed to get it to do so far.

---

### Post by jebus_beler on 2011-04-25
Thanks for the responses guys. 

I asked this elsewhere but maybe this would be a better place:

I was hoping to only get a bluetooth keyboard but I have to install linux on the system and i'm guessing bluetooth won't work on the boot cd or without some tweaking so I probably need to buy a usb keyboard as well.  Can anyone confirm (or deny) this?

---

### Post by psusi on 2011-04-25
I would think that a motherboard with built in bluetooth would have bios support for it at boot time.

---

### Post by rwsmith61 on 2011-04-26
OK. We're way off topic but I bought the Logitech Wirless MK710 that uses their mico universal adapter (its bluetooth) and it works with the UEFI BIOS.

I just bought the ASUS P8P67 rev B3 board with the Intel Core i7 2600K processor. I can't overclock because the stock fan is an inefficient cooler (replaced the heat paste twice).

I got an minimum OC system with 40/102.5 but was needing the temperature sensors and found this thread to be excellent at providing me what I needed to know. So, I may still back off the OC because all cores are at +95.0C (hey, I'm trying to increase my BOINC stats the 20 hours I work and sleep ;-)

The upgraded fan will be in next months budget and hope to get a few more Ghz out this rig, maybe even to the 5Ghz that others are reporting, but I will only do that if I can monitor my temperature.

Keep up the excellent work (my software days are over...oops TMI ;-)

--bs

---

### Post by paulisdead on 2011-04-27
> **rwsmith61 said:**
> OK. We're way off topic but I bought the Logitech Wirless MK710 that uses their mico universal adapter (its bluetooth) and it works with the UEFI BIOS.

I just bought the ASUS P8P67 rev B3 board with the Intel Core i7 2600K processor. I can't overclock because the stock fan is an inefficient cooler (replaced the heat paste twice).

I got an minimum OC system with 40/102.5 but was needing the temperature sensors and found this thread to be excellent at providing me what I needed to know. So, I may still back off the OC because all cores are at +95.0C (hey, I'm trying to increase my BOINC stats the 20 hours I work and sleep ;-)

The upgraded fan will be in next months budget and hope to get a few more Ghz out this rig, maybe even to the 5Ghz that others are reporting, but I will only do that if I can monitor my temperature.

Keep up the excellent work (my software days are over...oops TMI ;-)

--bs

Wow, and I was uncomfortable with going further since I was already seeing 60C+ temps at 4.4ghz during a 4 or 5 hour handbrake session.  How hot do these chips have to get before they stop giving you your full turbo speed, anyways?  I verified with turbostat that mine's still running all 4 cores at 4.4ghz throughout my encoding with handbrake.  I haven't really felt like pushing it much more, since I got this far without having to increase the voltages at all.

---

### Post by psusi on 2011-04-27
> **rwsmith61 said:**
> 
I just bought the ASUS P8P67 rev B3 board with the Intel Core i7 2600K processor. I can't overclock because the stock fan is an inefficient cooler (replaced the heat paste twice).


I'm just using the stock fan on my core i5-2500K and have pushed it from the stock 3.3 GHz to 4.3 GHz.  I'm sure I could go higher with better fan, but I'm happy with the performance and lower power consumption so I usually keep it at 3.4 GHz with 3.8 turbo boost.

The one thing that bugs me about the stock fan is that it refuses to turn off.  Apparently Intel hard wires their fans to have a minimum speed of about 30%.  Very annoying when the system is running idle and cool and I can't get it to be quiet.

---

### Post by jebus_beler on 2011-04-29
> **rwsmith61 said:**
> 

I just bought the ASUS P8P67 rev B3 board with the Intel Core i7 2600K processor. I can't overclock because the stock fan is an inefficient cooler (replaced the heat paste twice).



Somehow I haven't been able to find out a reply to this question but perhaps you can tell me since you're already running Ubuntu on the i7.  Does Ubuntu support hyperthreading?  Do you know which applications take advantage of it?  I'm interested in mathematica and bibble but other apps might still help motivate me to go for the i7 over the i5.  But at a minimum I wanna know if the OS supports it.

Thanks

---

### Post by ian dobson on 2011-04-29
Hi,

Ubuntu supports hyperthreading, it treats the "virtual" cpu's as normal CPU's and schedules tasks for them as normal.

I have a heavly threaded computational program (Folding) and when it runs at 100% I see a CPU load of 800% in top with hyperthreading enabled.

Regards
Ian Dobson

---

### Post by jebus_beler on 2011-04-29
Thanks.  Does it matter if I use the 64 or 32 bit version of ubuntu?  I guess for more than 4 gb of ram I need the 64 bit version.

---

### Post by ian dobson on 2011-04-29
If you want to use more than 4Gb ram, i'd go with 64bit. It is possible to use more than 4Gb on a 32bit system using a pae kernel, but it's more trouble than it's worth.

Regards
Ian Dobson

---

### Post by rwsmith61 on 2011-04-30
I am running Ubuntu 11.04 in 32-bit mode (my previous cpu was 32-bit) with 8GB of RAM (Corsair Vengence DDR3-1600). Ubuntu automatically loaded the pae kernel and I am not having any problems. I'll leave the 64-bit kernel for my servers when I get them upgraded.

Since my last post I have enabled the TPU and EPU switches on my ASUS P8P67 MB. This has brought the temperature down into the 80+ range but while also allowing me to run the BCLK/PEG and ratio at 103/43. 

Does anyone have any experience with the Corsair Hydro Series™ H70? This is what I am thinking of getting next month to keep my i7 cooler. What coolers are you running on your OC i5 or i7?

---

### Post by jebus_beler on 2011-04-30
I just setup my system with a Scythe Mugen 2 rev b cooler but i'm still not confident enough in the setup to start over-clocking it.  

I want to first get reliable CPU temps and fan speeds.  I'm running ubuntu 11.04 and sensors only prompted me to run the coretemp module.  That seems to show me 4 cpu temps.  Is the consensus that these are accurate?

I downloaded the module listed earlier in this thread and compiled it but when I tried to insmod it I got some symbol incompatibility problem.  I didn't run make install cause I wanted to make sure the module would load first -- could that be the problem?  I'm not sure how recently 11.04 came out but is this module supposed to work with the kernel in 11.04?

---

### Post by jebus_beler on 2011-04-30
Sorry but a further update.  I just ran a make install and the module installed fine so now with the w83627ehf and coretemp installed sensors gives me the following rather dubious output:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +28.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +26.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +35.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +0.90 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:        +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Vbat:         +3.30 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         674 RPM  (min =    0 RPM)  ALARM
fan2:         365 RPM  (min =    0 RPM)  ALARM
fan3:        1095 RPM  (min =    0 RPM)  ALARM
fan4:         763 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +30.5°C                                    
cpu0_vid:    +2.050 V


Note the negative CPUTIN temperature (whatever that is).  I'm not running a liquid nitrogen cooled system ;->  So any ideas why this output is so funky?

By the way do you know which of these fans is which?  My motherboard labels the fans chassis 1, chassis 2, cpu and power with the first three being bios controllable I think.  Any idea how this maps onto fans 1-4 above?  My board is the p8p67 pro b3 revision.

---

### Post by paulisdead on 2011-04-30
> **rwsmith61 said:**
> Does anyone have any experience with the Corsair Hydro Series™ H70? This is what I am thinking of getting next month to keep my i7 cooler. What coolers are you running on your OC i5 or i7?

No water cooling here, but I've got the Corsair A70 on my i7 2600k.  A big mamba-jamba heat pipe cooler with a couple 120mm fans on it.  Like I said earlier, I've got mine at 4.43ghz for it's max turbo.  It's a warm day, and I'm playing with handbrake on the prisoner blu rays, so coretemp is reporting 65C as the highest of each of the 4 cores under full load.  Idle is around 28C.

I think I didn't get the best contact with the thermal paste as I could have.  I've been meaning to pop it off and try again, just been lazy.

---

### Post by ian dobson on 2011-05-01
> **jebus_beler said:**
> Sorry but a further update.  I just ran a make install and the module installed fine so now with the w83627ehf and coretemp installed sensors gives me the following rather dubious output:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +28.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +26.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +35.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +0.90 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:        +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Vbat:         +3.30 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         674 RPM  (min =    0 RPM)  ALARM
fan2:         365 RPM  (min =    0 RPM)  ALARM
fan3:        1095 RPM  (min =    0 RPM)  ALARM
fan4:         763 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +30.5°C                                    
cpu0_vid:    +2.050 V


Note the negative CPUTIN temperature (whatever that is).  I'm not running a liquid nitrogen cooled system ;->  So any ideas why this output is so funky?

By the way do you know which of these fans is which?  My motherboard labels the fans chassis 1, chassis 2, cpu and power with the first three being bios controllable I think.  Any idea how this maps onto fans 1-4 above?  My board is the p8p67 pro b3 revision.

The CPUTIN is incorrect/the sensor isn't wired up. Here's my configuration for my p8p67 (just add it to /etc/sensors3.conf)

```
# nct6776 values for Asus p8p67 pro
    label temp1 "MB"
    set temp1_max 38
    set temp1_max_hyst 35

    ignore temp2

    label temp3 "CPU"

    set fan1_min 200
    set fan2_min 400
    set fan3_min 300
    set fan4_min 200
    ignore fan5

    label in0 "Vcore"
    set in0_min  1.1 * 0.9
    set in0_max  1.1 * 1.15

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.95
    set in1_max  12 * 1.1

    label in2 "AVCC"
    set in2_min  3.3 * 0.95
    set in2_max  3.3 * 1.1

    label in3 "+3.3V"
    set in3_min  3.3 * 0.95
    set in3_max  3.3 * 1.1

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.95
    set in4_max  5 * 1.1

    ignore in5

    label in7 "3VSB"
    set in7_min  3.3 * 0.95
    set in7_max  3.3 * 1.1

    label in8 "Vbat"
    set in8_min  3.3 * 0.95
    set in8_max  3.3 * 1.1
```

To findout which fan is atteched to which input just run watch sensors from the terminal and manually stop one fan after the other and see which fan slows down.

Regards
Ian Dobson

---

### Post by jebus_beler on 2011-05-01
Thanks a lot for the response Ian and for the driver!

Should the lines you gave me to add to /etc/sensors3.conf not be preceded by a "chip" label?  The file currently seems to have a lot of configuration options for various chips each with a chip "name" header.

No doubt this is a very basic question but can you set the fan's speeds or min speeds from lm-sensors -- you seem to be doing that in your config file.  I thought these asus boards only let you control three out of the four fans.

For the CPUTIN my bios does seem to give me the cpu temperature information and its not a number that shows up in any of the sensors output (sensors shows the cores running ~30C while the bios shows the CPU at ~45C). Is there something I'm supposed to connect up to let CPUTIN be read?  I haven't enabled TPU or EPU -- could that be the problem?

---

### Post by jebus_beler on 2011-05-01
This is a bit off-topic but to address my own earlier question about the motherboard compatibility with linux it seems that bluetooth works quite well out of the box with ubuntu 11.04.

---

### Post by ian dobson on 2011-05-01
> **jebus_beler said:**
> Thanks a lot for the response Ian and for the driver!

Should the lines you gave me to add to /etc/sensors3.conf not be preceded by a "chip" label?  The file currently seems to have a lot of configuration options for various chips each with a chip "name" header.

No doubt this is a very basic question but can you set the fan's speeds or min speeds from lm-sensors -- you seem to be doing that in your config file.  I thought these asus boards only let you control three out of the four fans.

For the CPUTIN my bios does seem to give me the cpu temperature information and its not a number that shows up in any of the sensors output (sensors shows the cores running ~30C while the bios shows the CPU at ~45C). Is there something I'm supposed to connect up to let CPUTIN be read?  I haven't enabled TPU or EPU -- could that be the problem?

Yep. you need to add the line 
chip "nct6775-*" "nct6776-*"

above text I gave you.
The CPUTIN just doesn't work, ASUS didn't wire up the input on the motherboard.

Have a look at the fancontrol program to control your fan speeds.

Regards
Ian Dobson

---

### Post by rwsmith61 on 2011-05-02
Not sure if all of the boards/user guides for the P8P67 use the same fan designators but here are the fan mappings for the nct6776 based on my rev B3 board and guide (my ref page 2-27):

PWR_FAN1 --> fan3
CPU_FAN  --> fan2
CHA_FAN1 --> fan1
CHA_FAN2 --> fan4

Merge the following lines to sensors3.conf for chip "nct6776-*":

label fan1 "Chassis1"
label fan2 "CPU"
label fan3 "Power"
label fan4 "Chassis2"

Of course you can rename the quoted strings to match your rig. If you don't use a fan then just add for example:

ignore fan3

After running sensors -s, you should get something similar to the following output:

```

# sensors
radeon-pci-0100
Adapter: PCI adapter
temp1:       +53.0°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +65.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +73.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +75.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +65.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +0.94 V  (min =  +0.99 V, max =  +1.26 V)   ALARM
+12V:        +12.19 V  (min = +11.42 V, max = +13.25 V)   
AVCC:         +3.34 V  (min =  +3.14 V, max =  +3.63 V)   
+3.3V:        +3.34 V  (min =  +3.14 V, max =  +3.63 V)   
+5V:          +5.04 V  (min =  +4.76 V, max =  +5.52 V)   
3VSB:         +3.46 V  (min =  +3.14 V, max =  +3.63 V)   
Vbat:         +3.38 V  (min =  +3.14 V, max =  +3.63 V)   
Chassis:     1284 RPM  (min =  200 RPM)
CPU:         2000 RPM  (min =  400 RPM)
Disks:       1195 RPM  (min =  200 RPM)
MB:           +33.0°C  (high = +38.0°C, hyst = +35.0°C)  sensor = thermistor
CPU:          +52.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +64.0°C                                    
cpu0_vid:    +2.050 V

```

Bob
--bs

---

### Post by jebus_beler on 2011-05-02
Thanks rwsmith61.  I have a p8p67 pro and the fan designations you give match the numbers I'm getting (by comparing the bios figures with what linux is reporting).

Out of curiosity the sensors output you gave was not while the system was idle right?  Your rpms and temps are way higher than mine.

---

### Post by rwsmith61 on 2011-05-02
> **jebus_beler said:**
> Thanks rwsmith61.  I have a p8p67 pro and the fan designations you give match the numbers I'm getting (by comparing the bios figures with what linux is reporting).

Out of curiosity the sensors output you gave was not while the system was idle right?  Your rpms and temps are way higher than mine.

No, these are not system idle numbers. I'm running five simultaneous BOINC projects at 80% total CPU cycles. Today these numbers are lower than normal because a couple projects are awaiting updates.

Regards,
Bob
--bs


BOINC Stats todate:
[IMG]http://www.boincstats.com/signature/user_74123.gif[/IMG]

---

### Post by jebus_beler on 2011-05-03
Because of a really big problem with the nvidia drivers in 11.04 I'm considering installing ubuntu 10.04 (I think the driver problem also occurs for 10.10).  Does anyone have experience with this motherboard on 10.04?  Will the sensor module (w83627ehf) still compile and run on that version of ubuntu?

If you have an nvidia card and are running 11.04 I'd be curious to hear if you're having problems or not.  See:

[http://ubuntuforums.org/showthread.php?p=10764312#post10764312](http://ubuntuforums.org/showthread.php?p=10764312#post10764312)

---

### Post by paulisdead on 2011-05-03
> **jebus_beler said:**
> Because of a really big problem with the nvidia drivers in 11.04 I'm considering installing ubuntu 10.04 (I think the driver problem also occurs for 10.10).  Does anyone have experience with this motherboard on 10.04?  Will the sensor module (w83627ehf) still compile and run on that version of ubuntu?

If you have an nvidia card and are running 11.04 I'd be curious to hear if you're having problems or not.  See:

[http://ubuntuforums.org/showthread.php?p=10764312#post10764312](http://ubuntuforums.org/showthread.php?p=10764312#post10764312)

Mine's been fine, but I used an older fix for this with CCSM.  Under General, click on Composite, and set the refresh rate to 120hz and make sure sync to vblank is on in nvidia-settings.

I have actually been having this odd quirk, that started happening when I got this video card, even on my old mobo.  Though it's been worse with this one, and seems to happen more often with natty.  Sometimes when I bootup, compiz is chewing up the cpu like crazy, and all GUI effects are severely laggy.  I had thought it was only after I booted to Ubuntu after playing a game in windows, and normally a full shutdown would fix it.  But today I had it happen on a clean startup after it being off all day.  I had to shutdown twice, in fact to get it to stop.

---

### Post by ian dobson on 2011-05-03
> **jebus_beler said:**
> Because of a really big problem with the nvidia drivers in 11.04 I'm considering installing ubuntu 10.04 (I think the driver problem also occurs for 10.10).  Does anyone have experience with this motherboard on 10.04?  Will the sensor module (w83627ehf) still compile and run on that version of ubuntu?

If you have an nvidia card and are running 11.04 I'd be curious to hear if you're having problems or not.  See:

[http://ubuntuforums.org/showthread.php?p=10764312#post10764312](http://ubuntuforums.org/showthread.php?p=10764312#post10764312)

The module compiles without any problems. I'm running mythtv on one of my boxes and I've not seen any problems with video playback.

Regards
Ian Dobson

---

### Post by jebus_beler on 2011-05-04
> **paulisdead said:**
> Mine's been fine, but I used an older fix for this with CCSM.  Under General, click on Composite, and set the refresh rate to 120hz and make sure sync to vblank is on in nvidia-settings.

I have actually been having this odd quirk, that started happening when I got this video card, even on my old mobo.  Though it's been worse with this one, and seems to happen more often with natty.  Sometimes when I bootup, compiz is chewing up the cpu like crazy, and all GUI effects are severely laggy.  I had thought it was only after I booted to Ubuntu after playing a game in windows, and normally a full shutdown would fix it.  But today I had it happen on a clean startup after it being off all day.  I had to shutdown twice, in fact to get it to stop.

I tried that fix but it didn't consistently do anything for me.  I don't know if it fixed the video and actually its not my main concern as I can live without video but its the random, unfixable slow-downs that pushed me to downgrade.  After running perfectly smoothly the windowing interface suddenly becomes very stuttery and windows drag very slowly.  As far as i can tell the only fix is a reboot.  Unlike you, however, my CPU usage never goes up ... the system is not loaded down at all.  It looks like a lot of people are having similar problems (though its not clear they're all the same).  How are you managing to use your system that way?

Btw I don't think this has anything to do with the motherboard -- i would have said its an nvidia issue but I've found a thread with ati users having the same problem.

Also, for those who might care it doesn't look like ubuntu 10.04 supports the onboard ethernet on the p8p67 pro (at least out of the box).

---

### Post by rwsmith61 on 2011-05-04
> Btw I don't think this has anything to do with the motherboard -- i would have said its an nvidia issue but I've found a thread with ati users having the same problem.

Now that you mentioned it, I had started to have problems with the windows and responsiveness. I had attributed it to the fact that I am running multiple BOINC jobs.

When I installed by P8P67 I upgraded to the ATI 4550. Although I don't see any problems with DRI/DRM in the Xorg.0.logs my compiz effects are noticably worse than with my original 10.10.

I'll take a look later for the ati thread and see if I am having the same issues.

---

### Post by paulisdead on 2011-05-04
For me, I only get the slowdown of effects on bootup, and only sometimes.  I can generally just restart and it's fine.  I have had a slowdown of effects happen on my laptop at work (nvidia mobile quadro), but the thing has to be running for like 2 months or so, it's likely not the same problem.

I'd love to figure out how to get rid of the drop shadows though.  They've been causing high def video to stutter when the window changes focus.  I tried all the options in CCSM, and the only way to kill the drop shadows was to kill the window decorations with it.

Now that I think about it, I did the 120hz tearing fix on this box without even checking if video was tearing.  I realize now that I didn't do it on the htpc box in the living room that has an nvidia card, and I use vdpau on.  I haven't noticed any tearing so far.

What players are you guys using?  I pretty much exclusively use smplayer on top of mplayer from the daily builds ppa.

---

### Post by ian dobson on 2011-05-04
Hi,

I'm not seeing any tearing on my MythTV box with vdpau playback in MythTV or vlc (pure software). The box is an underclocked Core2Duo and and NVidia 9600 graphic card.

Regards
Ian Dobson

---

### Post by jebus_beler on 2011-05-06
> **ian dobson said:**
> The module compiles without any problems. I'm running mythtv on one of my boxes and I've not seen any problems with video playback.

Regards
Ian Dobson

Hi Ian,

Perhaps I'm doing something stupid but I get the following error trying to compile the module on 10.04 with the 2.6.32 kernel (just the updated stock ubuntu kernel):

w83627ehf.c: In function ‘w83627ehf_find’:
w83627ehf.c:2369: error: implicit declaration of function ‘pr_warn’

---

### Post by qaws on 2011-05-06
I tried this module, but I cannot insert it:

```
insmod: error inserting 'w83627ehf.ko': -1 Device or resource busy
```

Any idea, how to fix it?

---

### Post by ian dobson on 2011-05-06
> **jebus_beler said:**
> Hi Ian,

Perhaps I'm doing something stupid but I get the following error trying to compile the module on 10.04 with the 2.6.32 kernel (just the updated stock ubuntu kernel):

w83627ehf.c: In function ‘w83627ehf_find’:
w83627ehf.c:2369: error: implicit declaration of function ‘pr_warn’

Hi,

Just edit the c file and change pr_warn to pr_info, that should do it.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-05-06
> **qaws said:**
> I tried this module, but I cannot insert it:

```
insmod: error inserting 'w83627ehf.ko': -1 Device or resource busy
```

Any idea, how to fix it?

Add acpi_enforce_resources=lax to your kernel commandline. The error your seeing is because the BIOS declares that it still controls the memory area used by the chip. The lax option tells the linux kernel to ignore what the BIOS says.

Regards
Ian Dobson

---

### Post by jebus_beler on 2011-05-07
> **ian dobson said:**
> Hi,

Just edit the c file and change pr_warn to pr_info, that should do it.

Regards
Ian Dobson

Thanks, that worked!

---

### Post by tnttrx on 2011-05-08
newer kernels have very useful **pkgtemp** module that seems to show the highest temperature of all CPU cores. I use this reading to set fan speeds in fancontrol.


> coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +67.0 C  (high = +80.0 C, crit = +98.0 C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +67.0 C  (high = +80.0 C, crit = +98.0 C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +62.0 C  (high = +80.0 C, crit = +98.0 C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +61.0 C  (high = +80.0 C, crit = +98.0 C)

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0:  +67.0 C  (high = +80.0 C, crit = +98.0 C)


---

### Post by ian dobson on 2011-05-08
> **tnttrx said:**
> newer kernels have very useful **pkgtemp** module that seems to show the highest temperature of all CPU cores. I use this reading to set fan speeds in fancontrol.

Hi,

But without the nct6776 module you don't have any fans to set, atleast not on a asus p8p67.

Regards
Ian Dobson

---

### Post by tnttrx on 2011-05-08
yes, I'm using manually compiled w83627ehf module, geuss it's from this post:

[http://ubuntuforums.org/showpost.php?p=10570303&postcount=20](http://ubuntuforums.org/showpost.php?p=10570303&postcount=20)

> sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +42.0 C  (high = +80.0 C, crit = +98.0 C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +42.0 C  (high = +80.0 C, crit = +98.0 C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +40.0 C  (high = +80.0 C, crit = +98.0 C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +40.0 C  (high = +80.0 C, crit = +98.0 C)

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0:  +42.0 C  (high = +80.0 C, crit = +98.0 C)

nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.91 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:         +3.39 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.42 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:          +3.31 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:          419 RPM  (min =    0 RPM)  ALARM
fan2:            0 RPM  (min =    0 RPM)  ALARM
fan3:          576 RPM  (min =    0 RPM)  ALARM
fan4:          604 RPM  (min =    0 RPM)  ALARM
fan5:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +36.0 C  (high =  +0.0 C, hyst =  +0.0 C)  ALARM  sensor = thermistor
CPUTIN:        -60.0 C  (high = +80.0 C, hyst = +75.0 C)  sensor = diode
AUXTIN:        +40.5 C  (high = +80.0 C, hyst = +75.0 C)  sensor = thermistor
PECI Agent 0:  +43.0 C  
cpu0_vid:     +2.050 V

---

### Post by ian dobson on 2011-05-08
> **tnttrx said:**
> yes, I'm using manually compiled w83627ehf module, geuss it's from this post:

[http://ubuntuforums.org/showpost.php?p=10570303&postcount=20](http://ubuntuforums.org/showpost.php?p=10570303&postcount=20)

Have a look on page 6 of this thread for the correct calculations for voltages.

Regards
Ian Dobson

---

### Post by tnttrx on 2011-05-08
thx. 
I've seen that, but I'm picking up raw voltages (from /sys/.../in?) and calculate them before storing in rrd. later, I use rrds to draw graphs. 
I rarely use output of 'sensors' command itself. 
the only voltage I could use and it's absent from chip readings is RAM (DDR3) voltage.

---

### Post by ambrosa on 2011-12-24
Only for a report.

Driver w83627ehf compiles and works fine in Xubuntu 11.10 (kernel 3.0.0-14) with Asus P8P67 LE and Core i7-2600 (not 'k') with a little automatic overclock made by Asus TPU (CPU runs at 3535 MHz instead of its default 3400Mhz)

Thanks for driver and sensors3.conf changes.
Temp and Fan values are the same compared with other Windows software.


:)

---

### Post by ambrosa on 2011-12-24
Added to my GitHub repo.

[https://github.com/ambrosa/Asus-P8P67-Ubuntu-lm-sensors-driver](https://github.com/ambrosa/Asus-P8P67-Ubuntu-lm-sensors-driver)

---

### Post by ian dobson on 2011-12-25
Hi,

You know that the driver nade it into Linux 2.6.39 don't you, so there's no need to manually compile, it should already be included.

Regards
Ian Dobson

---

### Post by ambrosa on 2011-12-25
First of all .... Merry Christmas

Yes, you have right and I'm an idiot

Module w83627ehf.ko is already present in /lib/modules/3.0.0-14-generic/kernel/drivers/hwmon/

But there is something strange.

1) sensors-detect doesn't detect presence of NCT6776F on motherboard.
P8P67 LE uses it: I run (in Win7 environment) the great [http://openhardwaremonitor.org/](http://openhardwaremonitor.org/) and NCT is detect and works fine.

2) I need to modprobe w83627ehf and run again sensors-detect. Now NCT* is detected
```

Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Nuvoton NCT6776F Super IO Sensors'                   Success!
    (address 0x290, driver `to-be-written')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

```

But at the end is not automatically preloaded
```


Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton NCT6776F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Note: there is no driver for Nuvoton NCT6776F Super IO Sensors yet.
Check http://www.lm-sensors.org/wiki/Devices for updates.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----

```
I need manually to add driver in /etc/modules
Really, this is not a problem, but sound strange.

After change applyed to /etc/sensors3.conf
```

chip "w83627ehf-*" "w83627dhg-*" "w83667hg-*" "nct6775-*" "nct6776-*"
    label temp1 "MB"
    label fan1 "Chassis1"
    label fan2 "CPU"
    label fan3 "Power"
    label fan4 "Chassis2"

    set temp1_max 38
    set temp1_max_hyst 35

    #ignore temp2
    label temp3 "CPU"

    set fan1_min 200
    set fan2_min 400
    set fan3_min 300
    set fan4_min 200
    ignore fan5

    label in0 "Vcore"
    set in0_min 1.1 * 0.9
    set in0_max 1.1 * 1.15

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min 12 * 0.95
    set in1_max 12 * 1.1

    label in2 "AVCC"
    set in2_min 3.3 * 0.95
    set in2_max 3.3 * 1.1

    label in3 "+3.3V"
    set in3_min 3.3 * 0.95
    set in3_max 3.3 * 1.1

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min 5 * 0.95
    set in4_max 5 * 1.1

    ignore in5

    label in7 "3VSB"
    set in7_min 3.3 * 0.95
    set in7_max 3.3 * 1.1

    label in8 "Vbat"
    set in8_min 3.3 * 0.95
    set in8_max 3.3 * 1.1                                         

```

"sensors" ignore min/max values giving ALARM for every value. But this sound as a lm-sensors issue.
And CPU temp is wrong (+65°C ??). The correct value looks to be "PECI Agent 0"
No problem to modify sensors3.conf : probably it's a P8P67 LE issue.

```

ambrosa:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +28.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +23.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +25.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +28.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +28.0°C  (high = +80.0°C, crit = +98.0°C)

nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +1.00 V  (min =  +0.00 V, max =  +1.74 V)
+12V:         +12.38 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+5V:           +5.20 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.44 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Chassis1:        0 RPM  (min =    0 RPM)  ALARM
CPU:          1256 RPM  (min =    0 RPM)  ALARM
Power:        1551 RPM  (min =    0 RPM)  ALARM
Chassis2:        0 RPM  (min =    0 RPM)  ALARM
MB:            +24.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        +90.5°C  (high = +81.0°C, hyst = +76.0°C)  ALARM  sensor = thermistor
CPU:           +65.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +27.5°C  
cpu0_vid:     +2.050 V

```

---

### Post by ian dobson on 2011-12-25
> **ambrosa said:**
> First of all .... Merry Christmas

Yes, you have right and I'm an idiot

Module w83627ehf.ko is already present in /lib/modules/3.0.0-14-generic/kernel/drivers/hwmon/

But there is something strange.

1) sensors-detect doesn't detect presence of NCT6776F on motherboard.
P8P67 LE uses it: I run (in Win7 environment) the great [http://openhardwaremonitor.org/](http://openhardwaremonitor.org/) and NCT is detect and works fine.

2) I need to modprobe w83627ehf and run again sensors-detect. Now NCT* is detected


Hmmm, I though that way fixed. I'll have a look at it tomorrow.

The w83627ehf module as existed for a very long time (from 2003?), and is the swiss army knife of modules supporting 7 different hw monitoring chips. In the beginning 2011 support for the nct677x was added.

OK, can you try editing sensors-detect and changing:-

```
                name => "Nuvoton NCT6776F Super IO Sensors",
                driver => "w83627ehf",
                devid => 0xC333,
                logdev => 0x0b,
                features => FEAT_IN | FEAT_FAN | FEAT_TEMP,
```

changing the "driver =>" line so the the driver name is included.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-12-25
Hi,

OK, I've had another look at sensors-detect and revision 5946 is the newest version. I'll create a diff and post it to the lm-sensors list sometime next week.

The diff won't be much more than the code I posted above.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-12-27
> **ambrosa said:**
> First of all .... Merry Christmas

"sensors" ignore min/max values giving ALARM for every value. But this sound as a lm-sensors issue.
And CPU temp is wrong (+65°C ??). The correct value looks to be "PECI Agent 0"


and a happy new year,

you need to run sensors -s to set the alarm limits.

Regards
Ian Dobson

---

### Post by mozart_ar on 2012-02-03
Hello, 

 Thanks, Ian Dobson. I have a HP dv7 , CPU Intel i5. I'm using ubuntu 10.04.

```
uname -a
Linux dv7-ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64 GNU/Linux
```

I've compiled the driver, but I got this output after the modprobe:

```
sudo modprobe w83627ehf 
FATAL: Error inserting w83627ehf (/lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/w83627ehf.ko): No such device

```

I tried boot using: acpi_enforce_resources=lax, but same result.

---

### Post by ian dobson on 2012-02-04
> **mozart_ar said:**
> Hello, 

 Thanks, Ian Dobson. I have a HP dv7 , CPU Intel i5. I'm using ubuntu 10.04.

```
uname -a
Linux dv7-ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64 GNU/Linux
```

I've compiled the driver, but I got this output after the modprobe:

```
sudo modprobe w83627ehf 
FATAL: Error inserting w83627ehf (/lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/w83627ehf.ko): No such device

```

I tried boot using: acpi_enforce_resources=lax, but same result.

Hi,

Are you sure the lax option is set. What do you see from:-
cat /proc/cmdline

Are you sure you actually installed the module in the correct directory? What do you see with:-

 ls -o /lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/w83627ehf.ko

Regards
Ian Dobson

---

### Post by mozart_ar on 2012-02-04
Hi Ian,

 my answer below:

> **ian dobson said:**
> 
Are you sure the lax option is set. What do you see from:-
cat /proc/cmdline

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=c8a4c0d2-8f64-4384-bdb8-fc0f2e1a7ec4 ro quiet splash acpi_enforce_resources=lax
```


> **ian dobson said:**
> 
Are you sure you actually installed the module in the correct directory? What do you see with:-

 ls -o /lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/w83627ehf.ko

```
-rw-r--r-- 1 root 67104 2012-02-04 11:04 /lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/w83627ehf.ko
```

Should I load coretemp ?

This is the output:
```
sudo modprobe coretemp
FATAL: Error inserting coretemp (/lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/coretemp.ko): No such device
```

---

### Post by ian dobson on 2012-02-04
> **mozart_ar said:**
> Hi Ian,

 my answer below:


```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=c8a4c0d2-8f64-4384-bdb8-fc0f2e1a7ec4 ro quiet splash acpi_enforce_resources=lax
```



```
-rw-r--r-- 1 root 67104 2012-02-04 11:04 /lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/w83627ehf.ko
```

Should I load coretemp ?

This is the output:
```
sudo modprobe coretemp
FATAL: Error inserting coretemp (/lib/modules/2.6.32-38-generic/kernel/drivers/hwmon/coretemp.ko): No such device
```

Hi,

Your running an old kernel, that could be your problem. Maybe try acpi_enforce_resources=no and to get coretemp working you'll need a newer version of it. Maybe you can install a backported kernel.

Regards
Ian Dobson

---

