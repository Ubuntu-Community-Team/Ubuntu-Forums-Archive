---
title: "How Do I add this driver to use with lm-sensors?"
date: 2012-10-04
forum: General Help
---

### Post by Wiking on 2012-10-04
Hi, I was trying to setup lm-sensors but my mobo was not supported.

I've been following this sticky: [http://ubuntuforums.org/showthread.php?t=42737]("http://ubuntuforums.org/showthread.php?t=42737")


Researching on the internet I found this driver available for my mobo (Asus p8z77-V): [https://github.com/groeck/nct6775]("https://github.com/groeck/nct6775")

Only thing is I don't know how to proceed from here. How do I install the driver? Will I have to run sensors-detect again after installing the driver?

```
wiking@admin:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +58.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +39.0°C  (high = +85.0°C, crit = +105.0°C)
Core 0:         +33.0°C  (high = +85.0°C, crit = +105.0°C)
Core 1:         +35.0°C  (high = +85.0°C, crit = +105.0°C)
Core 2:         +40.0°C  (high = +85.0°C, crit = +105.0°C)
Core 3:         +37.0°C  (high = +85.0°C, crit = +105.0°C)
```

That's my  output for now. ^^

---

### Post by habana on 2012-10-04
See this thread [http://ubuntuforums.org/showthread.php?t=2002668](http://ubuntuforums.org/showthread.php?t=2002668) particularly #6. This is for a different driver but the process should be the same. Note that you have to repeat the process after a kernel update.

---

### Post by Wiking on 2012-10-04
I don't know what I'm doing. What is the correct syntax for this?

I typed this, but I know it's wrong.

```
wiking@admin:~$ sudo make /home/wiking/Desktop/groeck-nct6775-87f60dd
[sudo] password for wiking: 
make: Nothing to be done for `/home/wiking/Desktop/groeck-nct6775-87f60dd'.
wiking@admin:~$ sudo make /home/wiking/Desktop/groeck-nct6775-87f60dd
make: Nothing to be done for `/home/wiking/Desktop/groeck-nct6775-87f60dd'.
wiking@admin:~$ sudo make /home/wiking/Desktop/groeck-nct6775-87f60dd/Makefile
make: Nothing to be done for `/home/wiking/Desktop/groeck-nct6775-87f60dd/Makefile'.
wiking@admin:~$ 

```

There are 4 files in the folder:

compat.h
lm75.h
Makefile
nct6775.c

and

README

---

### Post by Wiking on 2012-10-04
```
wiking@admin:~$ cd /usr/local/src
wiking@admin:/usr/local/src$ make
  CC [M]  /usr/local/src/nct6775.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/local/src/nct6775.mod.o
  LD [M]  /usr/local/src/nct6775.ko
wiking@admin:/usr/local/src$ sudo make install
cp nct6775.ko /lib/modules/3.2.0-29-generic/kernel/drivers/hwmon
depmod -a -F /boot/System.map-3.2.0-29-generic 3.2.0-29-generic
wiking@admin:/usr/local/src$ 
```

So that's what I got when I tried compiling it, however when I ran sensors-detect it only found:

```
 
#----cut here----
# Chip drivers
coretemp
#----cut here----

```

Same old drivers for the CPU as before. And I still get the same results as before when I use sensors.

---

### Post by habana on 2012-10-05
Firstly I suggest you make a folder in your home directory for the files you have downloaded. The reason for this is you will have to repeat the install procedure after a kernel update so you need to keep these files and you don't want to clutter your Desktop.

I note there are two .h files and suspect the only one you need is the compat.h file.

Navigate to this folder and type ```
sudo make
```
Then type ```
sudo make install
```

If you now look into the folder you created you should see some new files (object files) something like nct6775.ko, nct6775.o.

You now need to edit your etc/modules file. Add a single line ```
nct6775
``` or whatever the .ko and .o files are called.

Restart your computer and run ```
sudo sensors-detect
```

That's it. Good luck!

---

### Post by pbrane on 2012-10-05
You should not need to 'make' the driver as root. Only 'make install' as root. you can run 'sudo modprobe nct6775' to load the driver to see if it works. if it does, then you can add 'nct6775' to your /etc/modules file. no need to add that line unless the driver does what you want. to remove the driver you'll need to 'sudo modprobe -r nct6775', then 'sudo make uninstall'. So create that directory habana talked about and keep the source available.

---

### Post by Wiking on 2012-10-05
```
wiking@admin:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +59.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +38.0°C  (high = +85.0°C, crit = +105.0°C)
Core 0:         +33.0°C  (high = +85.0°C, crit = +105.0°C)
Core 1:         +34.0°C  (high = +85.0°C, crit = +105.0°C)
Core 2:         +38.0°C  (high = +85.0°C, crit = +105.0°C)
Core 3:         +34.0°C  (high = +85.0°C, crit = +105.0°C)

nct6779-isa-0290
Adapter: ISA adapter
in0:                    +0.82 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.00 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.38 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.38 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.44 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.06 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                   +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +0.26 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +0.18 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   737 RPM  (min =    0 RPM)
fan2:                  1005 RPM  (min =    0 RPM)
fan3:                  1430 RPM  (min =    0 RPM)
fan4:                   821 RPM  (min =    0 RPM)
fan5:                     0 RPM  (min =    0 RPM)
SYSTIN:                 +35.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:                 +34.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:                -62.0°C    sensor = thermistor
AUXTIN1:                -62.0°C    sensor = thermistor
AUXTIN2:                -62.0°C    sensor = thermistor
AUXTIN3:                -62.0°C    sensor = thermistor
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
PCH_MCH_TEMP:            +0.0°C  
cpu0_vid:              +0.000 V
intrusion0:            ALARM
intrusion1:            ALARM
```

thanks

---

