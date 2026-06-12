---
title: "Problem with lm-sensors"
date: 2010-01-20
forum: General Help
---

### Post by gabe17 on 2010-01-20
Hi! I have been using lm-sensors for some time without any problems, but yesterday I changed my CPU (before: AMD Athlon X2 4600+, NOW: AMD Athlon X2 7750 BE) and now the sensors which should show the CPU temperature don't work. I tried sensors-detect, but without success. Could somebody help me? Thx. 
 
P.S. The sensor that shows CPU temperature in BIOS works.

---

### Post by Yellow Pasque on 2010-01-20
Both CPU's should use k8temp module. Maybe try a more recent version of lm-sensors? [https://launchpad.net/~ari-tczew/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~ari-tczew/+archive/ppa?field.series_filter=karmic)

---

### Post by gabe17 on 2010-01-20
No, the new one should use K10 I think...see: 
[http://www.cpu-world.com/CPUs/K10/AMD-Athlon](http://www.cpu-world.com/CPUs/K10/AMD-Athlon) X2 7750 Black Edition - AD775ZWCJ2BGH (AD775ZWCGHBOX).html

---

### Post by Yellow Pasque on 2010-01-20
Oh, well if it's K10 then.. :P
```
cd /opt
sudo mkdir k10; cd k10/
sudo wget http://khali.linux-fr.org/devel/misc/k10temp/Makefile
sudo wget http://khali.linux-fr.org/devel/misc/k10temp/k10temp.c
sudo make && sudo make install
sudo depmod -a
sudo modprobe k10temp
```
Joy? If module builds and fails to load, check end of dmesg:
```
dmesg | tail -n 10
```

---

### Post by gabe17 on 2010-01-21
```

/opt/k10$ sudo make && sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /opt/k10/k10temp.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /opt/k10/k10temp.mod.o
  LD [M]  /opt/k10/k10temp.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
cp k10temp.ko /lib/modules/2.6.31-17-generic/kernel/drivers/hwmon
depmod -a -F /lib/modules/2.6.31-17-generic/build/System.map 2.6.31-17-generic
FATAL: Could not open '/lib/modules/2.6.31-17-generic/build/System.map': No such file or directory
make: *** [modules_install] Error 1

```

no success...

---

### Post by Yellow Pasque on 2010-01-21
I got that error too. I am still able to load the kernel module.
```
sudo depmod -a
sudo modprobe -v k10temp
```
If that is successful, run sensors-detect again:
```
sudo sensors-detect
```

---

### Post by gabe17 on 2010-01-21
```

/opt/k10$ sudo depmod -a
/opt/k10$ sudo modprobe -v k10temp
/opt/k10$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-nforce2' for device 0000:00:01.1: nVidia Corporation nForce4 SMBus (MCP55)

We will now try to load each adapter module in turn.
Module `i2c-nforce2' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus nForce2 adapter at 1c00 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus nForce2 adapter at 1c40 (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7475'...                     Success!
    (confidence 5, driver `to-be-written')
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Winbond W83791D'...                            No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found `ITE IT8716F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 1c40'
    Busdriver `i2c-nforce2', I2C address 0x2e
    Chip `Analog Devices ADT7475' (confidence: 5)
  * Chip `AMD K10 thermal sensors' (confidence: 9)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `ITE IT8716F Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
# Chip drivers
# no driver for Analog Devices ADT7475 yet
it87
#----cut here----

Do you want to add these lines automatically? (yes/NO)y
/opt/k10$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.15 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +3.23 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:         +4.81 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +11.52 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:        +4.73 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +2.98 V
fan1:       1358 RPM  (min =    0 RPM)
fan2:       1016 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +40.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +40.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +21.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.638 V

```

I am able to load the module too, but still no success. :(

---

### Post by Yellow Pasque on 2010-01-21
Sadly, I don't think your CPU will ever be supported: [http://lkml.org/lkml/2009/11/20/97](http://lkml.org/lkml/2009/11/20/97)

---

### Post by gabe17 on 2010-01-21
That's not very good...monitoring the temperature of this CPU is very important for me, because of overclocking. 

> 
The alternative already exists: you can rebuild the driver yourself
without this check.
Is it really possible to rebuild it?

---

### Post by Yellow Pasque on 2010-01-21
> Is it really possible to rebuild it?
The driver has already been patched to have a force option for CPU's with bogus sensors (sudo modprobe k10temp force=1), but if it loads, then maybe your CPU is okay? Maybe you just need a newer version of lm-sensors?

---

### Post by gabe17 on 2010-01-22
The CPU is surely OK. It seems that I don't have the latest version of lm-sensors. My actually installed version is:
```
$ sensors -v
sensors version 3.0.2 with libsensors version 3.0.2

```

And the latest version is 3.1.1. How can I install the latest one?

---

### Post by gabe17 on 2010-01-22
Finally, I found the solution here:
[http://ubuntuforums.org/showthread.php?p=7871888#post7871888](http://ubuntuforums.org/showthread.php?p=7871888#post7871888)

SOLVED

---

