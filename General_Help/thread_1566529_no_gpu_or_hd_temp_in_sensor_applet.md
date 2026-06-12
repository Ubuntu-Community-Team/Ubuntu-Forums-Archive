---
title: "no gpu or hd temp in sensor applet"
date: 2010-09-02
forum: General Help
---

### Post by RUBICON_4X4 on 2010-09-02
i just recently put ubuntu on my friends computer and and when i gave him the sensor applet he had a nice list of sensors to choose from, cpu temp, mb temp, fan speeds, voltages, but he also has all the hd temps and gpu temp.  im just wondering how i can get these on my applet.  i can get the hd temp when i go into the disk utility so i know what there is a sensor in it and the video card is a radeon 4800 series so im assuming there is a sensor in it.  when i type sensors into terminal all i get is >>

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.50 V  (min =  +0.85 V, max =  +1.70 V)
 +3.3 Voltage:       +3.50 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.08 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.64 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:         0 RPM  (min =  600 RPM)
CHASSIS FAN Speed:  2177 RPM  (min =  600 RPM)
CHASSIS FAN 2 Speed:1744 RPM  (min =  600 RPM)
CPU Temperature:     +44.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:      +33.0°C  (high = +45.0°C, crit = +75.0°C)  



        >>>  and when i do sensors-detect i get >>


# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: System manufacturer System Product Name
# Board: ASUSTeK Computer INC. M4A79XTD EVO

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
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
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
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK


but i still cant get the hd or gpu temps.

---

### Post by RUBICON_4X4 on 2010-09-07
???

---

### Post by Frogs Hair on 2010-09-07
Hi,

This may be helpful for monitoring  HDD tempeture , My GPU  sensor works with Nivida so I have no suggestion for that.  [http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html](http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html)

---

### Post by Frogs Hair on 2010-09-07
Command for hdd temp:  sudo hddtemp /dev/sda

---

### Post by RUBICON_4X4 on 2010-09-12
if i do that i can get the hd temp in terminal but i would like to see it in the applet. i have a duel boot setup and in windows i can go into the setting for the video card and it gives me the temp and load. is there anyway to get that in ubuntu?  i just think that its strange that my friends computer that i just threw ubuntu on had those sensors in the applet right off the bat,  could it be that he has a seagate hd vs my WD and a nvidia video card vs my ati?

---

### Post by carlenski on 2010-09-28
I had the same problem.  You need to have the hddtemp daemon started at boot and then it should appear
in the Sensors tab on the applet.

To start the hddtemp daemon go to /etc/defaults and edit the hddtemp file.  I needed to change the
RUN_DAEMON="false" to RUN_DAEMON="true"

reboot and check that the daemon is running:

tm@tm-sff-desktop:~$ ps aux | grep hdd
root      1112  0.0  0.0   4408   904 ?        S    16:16   0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sg1 /dev/sda

Now if you look in the hardware monitor applet preferences, on the Sensors tab  you should see the hddtemp sensor.

I don't know about the GPU, but it may be a similar issue.  Hope this helps

---

### Post by andrewthomas on 2010-09-28
> **RUBICON_4X4 said:**
>  the video card is a radeon 4800 series so im assuming there is a sensor in it. 
There is support for the radeon GPU temperature sensor in the 2.6.36 kernel.

---

