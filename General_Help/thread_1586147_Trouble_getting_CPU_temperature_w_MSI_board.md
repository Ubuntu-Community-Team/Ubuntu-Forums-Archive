---
title: "Trouble getting CPU temperature w/ MSI board"
date: 2010-10-01
forum: General Help
---

### Post by PPPP on 2010-10-01
Hi all,

So I just got a MSI 870A-G54 and have been trying to get the CPU temperature on the command line.  I ran the following

```
 sudo apt-get install lm-sensors hddtemp sensors-applet computertemp
```

And ran sensors-detect

```
sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: MSI MS-7599
# Board: MSI 870A-G54 (MS-7599)

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
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
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
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0x0909

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
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively):
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter:  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter:  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check http://www.lm-sensors.org/wiki/Devices for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK


```

When I executed "sensors", I got:
```

sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

What's wrong?

---

### Post by stRunF on 2010-10-01
is the CPU temperature showen in BIOS?

---

### Post by PPPP on 2010-10-01
Yes, I can see it.

---

### Post by stRunF on 2010-10-01
you installed the drivers properly?
be sure there are up-to-date also..

---

### Post by PPPP on 2010-10-01
I didn't install any extra drivers.  It's just the stock install.  What do I do to install the proper drivers?

---

### Post by stRunF on 2010-10-01
> **PPPP said:**
> I didn't install any extra drivers.  It's just the stock install.  What do I do to install the proper drivers?
sincerely i'm also new/beginner at ubuntu, hope that others will help you with ur prob :)
i just thought thar ur bios isn't showing the temp, that's why i replied ^^

---

### Post by PPPP on 2010-10-01
> **stRunF said:**
> sincerely i'm also new/beginner at ubuntu, hope that others will help you with ur prob :)
i just thought thar ur bios isn't showing the temp, that's why i replied ^^

Thanks for the try :)

And welcome to the community! :D

---

### Post by stRunF on 2010-10-01
> **PPPP said:**
> Thanks for the try :)

And welcome to the community! :D
thanks ):P

---

### Post by ajgreeny on 2010-10-01
I believe this failure is simply down to your particular set of hardware which may not have all the appropriate sensor chips etc etc, to let lm-sensors do its work.  I can never get it to run either, though my hardware is completely different to yours.

As a sort of workaround I have to use **hddtemp** for disk temperature, and **mbmon** for other hardware, though I am aware that these may not be as accurate as lm-sensors, or so I'm informed.

---

### Post by gandaran on 2010-10-01
does the sensors applet show the temperature? theres no need to run sensors-detect on new motherboards, the sensors applet will work without it.

---

### Post by PPPP on 2010-10-04
> **ajgreeny said:**
> I believe this failure is simply down to your particular set of hardware which may not have all the appropriate sensor chips etc etc, to let lm-sensors do its work.  I can never get it to run either, though my hardware is completely different to yours.

As a sort of workaround I have to use **hddtemp** for disk temperature, and **mbmon** for other hardware, though I am aware that these may not be as accurate as lm-sensors, or so I'm informed.

Thanks.  I still can't get the CPU temperature to show but hddtemp does work :)

---

### Post by PPPP on 2010-10-04
> **gandaran said:**
> does the sensors applet show the temperature? theres no need to run sensors-detect on new motherboards, the sensors applet will work without it.

No, the applet doesn't work for CPU...HD temperature applet does work though.

---

### Post by dgaud on 2010-10-07
You have a similar setup as I have with an AMD processor, so you you got the k10temp module problem.

```
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
```

You can try downloading the patched k10temp sourcecode from [here]("http://khali.linux-fr.org/devel/misc/k10temp/"). Then you need to extract to a folder and do this:

```
$ sudo make
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod
$ sudo modprobe k10temp
```

By the way... looks like your mobo is not yet supported by lm-sensors.

---

