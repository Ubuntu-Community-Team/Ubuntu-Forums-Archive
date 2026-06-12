---
title: "CPU thinks its cooler than it actually is"
date: 2009-07-26
forum: General Help
---

### Post by Chrus on 2009-07-26
I've been playing with Conky today. Got everything working, except for the CPU temp. Its constantly sitting on 40C. Doesn't matter how much load I put on it, it doesn't budge. When I go into the BIOS i get temps of 50+, and I can get them to change by putting load on the CPU.

acpi -t also gives 40C
```
Thermal 0: ok, 40.0 degrees C
```

So anyone know what the problem might be?

---

### Post by miegiel on 2009-07-26
Assuming you installed *sensors*, can you post the CLI output of ```
sensors
```

---

### Post by Chrus on 2009-07-26
Sensors is installed. Output:

```
chrus@Poseidon:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +31.0°C                                    
Core1 Temp:  +40.0°C                                    

w83791d-i2c-1-2d
Adapter: SMBus nForce2 adapter at 1c40
in0:         +1.38 V  (min =  +0.00 V, max =  +3.06 V)   
in1:         +1.20 V  (min =  +0.00 V, max =  +3.06 V)   
in2:         +2.58 V  (min =  +2.82 V, max =  +3.79 V)   ALARM
in3:         +3.04 V  (min =  +0.06 V, max =  +0.00 V)   ALARM
in4:         +0.96 V  (min =  +0.00 V, max =  +0.51 V)   ALARM
in5:         +1.58 V  (min =  +0.40 V, max =  +0.00 V)   ALARM
in6:         +1.55 V  (min =  +0.13 V, max =  +0.00 V)   ALARM
in7:         +2.99 V  (min =  +0.00 V, max =  +0.06 V)   ALARM
in8:         +3.18 V  (min =  +0.06 V, max =  +0.00 V)   ALARM
in9:         +1.94 V  (min =  +0.26 V, max =  +0.34 V)   ALARM
fan1:          0 RPM  (min = 1318 RPM, div = 8)  ALARM
fan2:       2556 RPM  (min =   -1 RPM, div = 8)  ALARM
fan3:          0 RPM  (min = 10546 RPM, div = 8)  ALARM
fan4:       2556 RPM  (min = 42187 RPM, div = 8)  ALARM
fan5:          0 RPM  (min =   -1 RPM, div = 8)  ALARM
temp1:       -48.0°C  (high = +64.0°C, hyst =  +0.0°C)  
temp2:       -48.0°C  (high = +80.0°C, hyst = +75.0°C)  
temp3:       -48.0°C  (high = +80.0°C, hyst = +75.0°C)  
cpu0_vid:   +0.775 V
beep_enable:enabled

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.41 V  (min =  +0.00 V, max =  +2.05 V)   
VDDR:        +1.84 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:       +3.33 V  (min =  +2.05 V, max =  +0.00 V)   ALARM
+5V:         +4.92 V  (min =  +0.05 V, max =  +0.00 V)   ALARM
+12V:       +12.03 V  (min = +10.24 V, max =  +0.00 V)   ALARM
in5:         +3.71 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in6:         +1.78 V  (min =  +0.00 V, max =  +0.13 V)   ALARM
5VSB:        +4.87 V  (min =  +0.03 V, max =  +0.22 V)   ALARM
VBat:        +3.14 V
fan1:       2710 RPM  (min = 3245 RPM)  ALARM
fan2:       3629 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)  ALARM
temp1:       +39.0°C  (low  =  +0.0°C, high = -128.0°C)  sensor = thermal diode
temp2:       +47.0°C  (low  =  +0.0°C, high =  +0.0°C)  sensor = thermistor
temp3:        -8.0°C  (low  =  +0.0°C, high = +32.0°C)  sensor = thermistor
cpu0_vid:   +1.550 V


```

---

### Post by miegiel on 2009-07-26
You might want to run *sensors-detect* again and check the *confidence* of the sensors it finds. For now I suspect the *temp1* or *temp2* of the *w83791d-i2c-1-2d* or *it8716-isa-0290* sensors is you true CPU temp. The *k8temp-pci-00c3* sensor is known to give false values.

My *.conkyrc* temperature line is :
```
temp	= ${hwmon 1 temp 1}C ${hwmon 1 temp 2}C ${hwmon 1 temp 3}C (cpu/sys/nb)
```
I hope this helps.

---

### Post by Chrus on 2009-07-26
sensor-detect gives me this:

```
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-nforce2' for device 0000:00:09.1: nVidia Corporation nForce4 SMBus (MCP55)

We will now try to load each adapter module in turn.
Module `i2c-nforce2' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
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
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus nForce2 adapter at 1c40 (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x1f
Probing for `Maxim MAX6650/MAX6651'...                      No
Client found at address 0x2d
Handled by driver `w83791d' (already loaded), chip type `w83791d'
Client found at address 0x2f
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Analog Devices ADT7470'...                     No
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
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `Fintek custom power control IC'...             No
Probing for `Winbond W83791D'...                            No
Client found at address 0x48
Handled by driver `dummy' (already loaded), chip type `dummy'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x49
Handled by driver `dummy' (already loaded), chip type `dummy'
    (note: this is probably NOT a sensor chip!)

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
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83791d' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 1c40'
    Busdriver `i2c-nforce2', I2C address 0x2d
    Chip `w83791d' (confidence: 6)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `ITE IT8716F Super IO Sensors' (confidence: 9)

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
# Chip drivers
w83791d
it87
k8temp
#----cut here----

Do you want to add these lines automatically? (yes/NO)n

```

Dont really know what im looking at there? Does that look right?

---

### Post by miegiel on 2009-07-26
> ```
Driver `w83791d' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 1c40'
    Busdriver `i2c-nforce2', I2C address 0x2d
    Chip `w83791d' (confidence: 6)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `ITE IT8716F Super IO Sensors' (confidence: 9)

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)
```

Go for the *it87* sensor, since it's got a 9 for confidence and the *w83791d* only gets a 6. Just delete the line in */etc/modules*.

---

### Post by Chrus on 2009-07-26
I think I've got it sorted. I put this in my conkyrc file
```
Temp: ${hwmon 3 temp 2}C
```

Looks to be giving me an accurate number.

Ill play with /etc/modules tomorrow and see if I can get that sorted, but I fixed what I really wanted to get working, so that's enough for now.

Thanks for the help mate.

Cheers

---

