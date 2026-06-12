---
title: "help please with temperature monitoring (thinkpad)"
date: 2011-12-29
forum: General Help
---

### Post by kozre on 2011-12-29
I ve tried to install lm sensors
everything was done through synaptic package manager 
installed 
 
lm-sensors
eep24c
libglui2c2
libglui-dev
sensord
hddtemp
sensors-applet
-----
sudo modprobe i2c-dev
-----
sudo dpkg-reconfigure hddtemp
-----

notebook **lenovo thinkpad edge 14 intel P6100 2mhz c ubuntu 10.04.3 4gb ddr3 250 hd ati radeon 5145**
So sensors-detect shows **No sensors detected**
sensors shows

> acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +95.0°C)            

> # sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: LENOVO 0578RE8 (laptop)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
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
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8502
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.
 

please help to read temperatures on both cores because later I want to configure my noisy cooler fan:(

desktop applet screenshot 
[IMG]http://picsave.ru/images/screenshot.png

---

### Post by kozre on 2011-12-29
may be i understand something wrong?

---

### Post by 2F4U on 2011-12-29
The temperature for one core is the same as for all the other cores. I have a six core processor and also get only one temperature.

---

