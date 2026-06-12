---
title: "LM  Sensors and ACPI Temperatures"
date: 2009-10-01
forum: General Help
---

### Post by narsaw on 2009-10-01
When I enter the sensors command I get:

```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +39.0°C  (crit = +60.0°C)                  
[COLOR="Red"][b]
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +59.0°C  (high = +74.0°C, crit = +100.0°C)  
[/b][/COLOR]
f71882fg-isa-0290
Adapter: ISA adapter
3.3V:        +3.33 V
Vcore:       +1.35 V  (max =  +2.04 V)   
Vdimm:       +1.74 V
Vchip:       +2.50 V
+5V:         +4.83 V
12V:        +13.96 V
5VSB:        +8.48 V
3VSB:        +3.30 V
Battery:     +3.07 V
CPU:        2215 RPM
System:     1625 RPM
Power:      3030 RPM
Aux:           0 RPM  ALARM
[COLOR="Red"][b]
CPU:         +39.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
[/b][/COLOR]
System:      +42.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = thermistor

```

Notice above that I have temps for Core 0, Core 1 and a CPU temp. There is like a 20 degree difference there. Which is correct.

My processor is:
```
model name      : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
```

If I enter:
%  acpi -t
```

Thermal 0: ok, 39.0 degrees C

```

---

### Post by narsaw on 2009-10-01
Anyone?

---

### Post by oldsoundguy on 2009-10-01
LM sensors applet will list the ambient computer temp FIRST .. that is the temp inside the box itself.
The NEXT temp listed will be the processor and if you selected it to display each core separately .. your third display will also be the processor.
The last temp (if you have a power supply that has a sensor) will be that.

Not sure where an on board sensor for the video card falls, as I do not have one in my machine.

Right now mine runs:
38C in the box
46C on the processor(hyperthreaded with a BIG CoolerMaster cooler)
32C in the power supply.

And the processor(s) run at 100% all the time as I crunch data for UC Berkeley via BOINC.

Now, as to why you are getting different readings, just how did you set it up?  The preferences should allow you to set it close to what you want to see.

---

### Post by narsaw on 2009-10-01
> **oldsoundguy said:**
> LM sensors applet will list the ambient computer temp FIRST .. that is the temp inside the box itself.
The NEXT temp listed will be the processor and if you selected it to display each core separately .. your third display will also be the processor.
The last temp (if you have a power supply that has a sensor) will be that.

Not sure where an on board sensor for the video card falls, as I do not have one in my machine.

Right now mine runs:
38C in the box
46C on the processor(hyperthreaded with a BIG CoolerMaster cooler)
32C in the power supply.

And the processor(s) run at 100% all the time as I crunch data for UC Berkeley via BOINC.

Now, as to why you are getting different readings, just how did you set it up?  The preferences should allow you to set it close to what you want to see.

Thanks for the reply.

I realize that the preferences have offsets that you can use to fine tune in lm_sensors, but I don't know if the 59 degree is correct or the 39 is correct?

After I get that answer I can manage the offsets. 

Anyone know why the two Cores are 59 and CPU is 39?

---

### Post by dcstar on 2009-10-01
> **narsaw said:**
> 
.......
Anyone know why the two Cores are 59 and CPU is 39?

CPU's can have their own internal temp sensors (for each core), and MBs can also have a CPU temp sensor. One or both may not be being reported correctly, as CPU vendors can change the formula required to report correct temps when they make manufacturing changes to the same model of CPU that they sell.

My AMD Athlon 64 X2 Brisbane core CPU reports different temp data than the original version, and Linux reports the core temps about 20C lower than it actually is (having been configured for the original version).

---

### Post by waapwoop1 on 2010-11-02
I need help with this too. 

When i type sensors, i get a long list:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +50.0°C  (crit = +256.0°C)                  
temp2:       +44.0°C  (crit = +105.0°C)                  
temp3:       +41.0°C  (crit = +105.0°C)                  
temp4:       +31.7°C  (crit = +105.0°C)                  
temp5:       +50.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (crit = +100.0°C)    



I have no idea what is temp1-temp5.  I assume core 0 and 1 are the 2 processors.

also when i type acpi-t I get

:~$ acpi -t
Thermal 0: ok, 0.0 degrees C
Thermal 1: ok, 31.7 degrees C
Thermal 2: ok, 41.0 degrees C
Thermal 3: ok, 43.0 degrees C
Thermal 4: ok, 45.0 degrees C

What does this mean? what is what?

---

### Post by waapwoop1 on 2010-11-08
anyone understand this?

---

### Post by waapwoop1 on 2010-11-21
anyone know why i get so many temperature readings?

---

### Post by oldsoundguy on 2010-11-21
install the sensors applet to your panel.  Once installed, right click and select preferences .. your list of active sensors will be there.  I selected CPU temp to be displayed .. you can select whatever you want.

---

### Post by dcstar on 2010-11-21
> **waapwoop1 said:**
> anyone know why i get so many temperature readings?

Because that is what **your** motherboard supplies to Linux.

Check with the motherboard manufacturer what temp is what.

---

