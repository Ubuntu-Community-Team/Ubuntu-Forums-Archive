---
title: "Problem with lm-sensors"
date: 2009-10-09
forum: General Help
---

### Post by Tapas Bose, India on 2009-10-09
Hallo everybody.
I have installed lmsensors via synaptic and add Hardware Sensor Monitor to my panel. But I do not get fan rotation applet n the panel. Also I have installed gdesklet. In gdesklet when I am trying to launch LMSensors with plotters ( Display lmsensors information about fan speed ), an applet launched but it does not show any information. When I am trying to  configure it said "No Fan Rotation sensors were found. Is lmsensors installed and working?" under Fan rotation tab.
Please help me..

---

### Post by Tapas Bose, India on 2009-10-09
Output by "sensors" :
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +256.0°C)                  
temp2:       +50.0°C  (crit = +90.0°C)                  
temp3:       +46.0°C  (crit = +105.0°C)                  
temp4:       +34.1°C  (crit = +90.0°C)                  
temp5:       +50.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +53.0°C  (high = +85.0°C, crit = +85.0°C)

---

### Post by Yellow Pasque on 2009-10-09
Assuming your sensor chip reports fan information and is supported by lm-sensors, then run:
```
sudo sensors-detect
```

---

### Post by Tapas Bose, India on 2009-10-09
I have done this many times. But nothing is happened. 
The output is:
> # sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Sorry, no supported PCI bus adapters found.

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
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x3600
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
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)y

Now what to do?

---

### Post by Yellow Pasque on 2009-10-09
> **Tapas Bose, India said:**
> Now what to do?

Nothing. Your sensor chip is unsupported by lm-sensors: [http://www.lm-sensors.org/ticket/2359](http://www.lm-sensors.org/ticket/2359)

---

