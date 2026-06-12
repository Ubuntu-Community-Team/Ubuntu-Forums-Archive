---
title: "Temperatures - Headache in Ubuntu."
date: 2009-09-11
forum: General Help
---

### Post by Hangwire on 2009-09-11
Hi, I'm in need of a tool that shows all the available info from all the available sensors in my computer. So far, I've tried the Hardware Sensors Monitor and the Computer Temperature monitor, I've installed lm_sensors sensors and ran sensors-detect. 


Here is the output of that command: 

```
nick@SatanShallTremble:~$ sudo gedit /home/nick/.conkyrc
^C
nick@SatanShallTremble:~$ conky
Conky: desktop window (14000a3) is subwindow of root window (13c)
Conky: window type - normal
Conky: drawing to created window (0x1a00001)
Conky: drawing to double buffer
^CConky: received SIGINT or SIGTERM to terminate. bye!
nick@SatanShallTremble:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x1f
Probing for `Maxim MAX6650/MAX6651'...                      No

Next adapter: SMBus I801 adapter at 0400 (i2c-3)
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
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
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

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)
nick@SatanShallTremble:~$ 

```

But when I look at the sensors in Hardware Sensors Monitor, it shows only 2 - for my HD and my Video Card. 
Conky scripts that actually **work** and display all of the sensors (somebody has to help me about which is which too) are more than welcome.

Any suggestions? 

Thank you.

~Nick A.

---

### Post by Hangwire on 2009-09-11
shamefull bump :(

---

### Post by relay_man on 2009-09-11
From the command line, please post the output of 

sensors

We'll go from there.

---

### Post by Hangwire on 2009-09-12
This is the output. 
```
nick@SatanShallTremble:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.07 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.20 V  (min =  +3.70 V, max =  +7.23 V)   ALARM
AVCC:        +3.31 V  (min =  +2.30 V, max =  +0.51 V)   ALARM
3VCC:        +3.31 V  (min =  +2.90 V, max =  +1.81 V)   ALARM
in4:         +1.36 V  (min =  +0.27 V, max =  +0.15 V)   ALARM
in5:         +1.59 V  (min =  +0.14 V, max =  +1.67 V)   
in6:         +4.33 V  (min =  +3.38 V, max =  +0.84 V)   ALARM
VSB:         +3.31 V  (min =  +1.02 V, max =  +0.02 V)   ALARM
VBAT:        +3.31 V  (min =  +0.10 V, max =  +0.42 V)   ALARM
Case Fan:      0 RPM  (min =   81 RPM, div = 128)  ALARM
CPU Fan:    2360 RPM  (min = 7336 RPM, div = 4)  ALARM
Aux Fan:       0 RPM  (min =   82 RPM, div = 128)  ALARM
fan4:          0 RPM  (min = 6750 RPM, div = 4)  ALARM
fan5:          0 RPM  (min = 8035 RPM, div = 4)  ALARM
Sys Temp:    +42.0°C  (high =  +4.0°C, hyst =  +6.0°C)  ALARM  sensor = thermistor
CPU Temp:    +41.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +34.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +3.100 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +41.0°C  (high = +76.0°C, crit = +100.0°C)  

```

---

### Post by Hangwire on 2009-09-12
Anyone...?

---

### Post by ikisham on 2009-09-20
As you can see from the sensors command your monitoring modules are working ok so it's just a matter of finding a proper Conky config. Try [here]("http://crunchbanglinux.org/wiki/conky").

You can have the infos displayed on your panel too. Just install sensors-applet:
```
sudo apt-get install sensors-applet
```
then right click a panel, select 'add to panel' and choose the sensors applet. You'll be able to choose to display any of those infos you got from the sensors command.

Regards.

*Edit- sorry for that devilish emoticon, don't know how it got there...*

---

