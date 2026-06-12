---
title: "lm-sensors output from AMD E-450"
date: 2011-10-12
forum: General Help
---

### Post by moteprime on 2011-10-12
Hi.
I'm trying to setup "Hardware Sensors Indicator" in my panel, and it works fine.
But i get the output, here from lm-sensors

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +97.0°C)
temp2:        +40.0°C  (crit = +126.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +49.5°C  (high = +70.0°C)
                       (crit = +100.0°C, hyst = +97.0°C)

But what is that, Virtual Device and PCI adapter?
I'm using a Lenovo S205, AMD fusion E-450 APU.

---

### Post by dcstar on 2011-10-13
> **moteprime said:**
> Hi.
I'm trying to setup "Hardware Sensors Indicator" in my panel, and it works fine.
But i get the output, here from lm-sensors

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +97.0°C)
temp2:        +40.0°C  (crit = +126.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +49.5°C  (high = +70.0°C)
                       (crit = +100.0°C, hyst = +97.0°C)

But what is that, Virtual Device and PCI adapter?
I'm using a Lenovo S205, AMD fusion E-450 APU.

Did you run **sensors-detect**?

---

### Post by moteprime on 2011-10-13
Yes.
Here are the output:

# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: LENOVO 1038D4G (laptop)
# Board: LENOVO Inagua

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   Success!
    (driver `k10temp')
Intel digital thermal sensor...                             No
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
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
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

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
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

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 12h and 14h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK
Unloading cpuid... OK

---

### Post by mcduck on 2011-10-13
> **moteprime said:**
> Hi.
I'm trying to setup "Hardware Sensors Indicator" in my panel, and it works fine.
But i get the output, here from lm-sensors

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +97.0°C)
temp2:        +40.0°C  (crit = +126.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +49.5°C  (high = +70.0°C)
                       (crit = +100.0°C, hyst = +97.0°C)

But what is that, Virtual Device and PCI adapter?
I'm using a Lenovo S205, AMD fusion E-450 APU.
Impossible to say for sure, lm-sensors simply reads whatever data it gets from any hardware sensors it can detect. It doesn't know what the sensors are monitoring, or how the data they give should be interpreted. It's up to the user to edit the /etc/sensors.conf to point different sensor readings to suitable sensor names, and if necessary tell lm-sensors how the real value should be calculated from the raw sensor reading. And of course to set sane min/max/alarm values for different readings.

Anyway, acpiz-virtual-0 is most likely your motherboard's sensor chip, one sensor for the CPU socket and the other one somewhere around the motherboard for case ambient temperature. It's a virtual device because the infomration is sent to the system using ACPI, not by directly accessing te sensor chip itself. And the k10temp-pci-00c3 would most likely be the CPU's core temperature sensor (the "pci" in the name simply tells that the sensor uses PCI bus to communicate with your motherboard)

---

### Post by Mark Phelps on 2011-10-13
Those temps, especially if they're idle temps, seem really high.

I've got an AMD3 CPU on a Gigabyte motherboard and the idle temps are in the mid to upper 20's.

One thing I had to do to get the sensors read correctly was to append "acpi_enforce_resources=lax" to my "kernel" line in /etc/default/grub.

You can try that.  Then run "sudo update-grub". Reboot.

Then, check sensors again to see what readings you get this time.

---

### Post by moteprime on 2011-10-13
@mcduck

Thank you for the answer. I thought i would be something like that.
So i guess i have to find the information about which  sensors are what for my particular laptop somewhere.
You also mention "And of course to set sane min/max/alarm values for different readings". Doesn't my laptop have control over these things, have i changed anything by installing the sensors? I would really be more confident that it managed it by itself, and not that i risk messing anything up.

---

### Post by moteprime on 2011-10-13
@Mark Phelps

>  "acpi_enforce_resources=lax" to my "kernel" line in /etc/default/grub.

What does it do?
My laptop does not seem to be especially hot, would it not be more likely that it is the sensor program that does not know how to interpret the readings it get. It does not seem to know the devices it is reading?
If it is running hot, does the BIOS not control the fan so that it will cool it down?

---

### Post by mcduck on 2011-10-13
> **moteprime said:**
> @mcduck

Thank you for the answer. I thought i would be something like that.
So i guess i have to find the information about which  sensors are what for my particular laptop somewhere.
You also mention "And of course to set sane min/max/alarm values for different readings". Doesn't my laptop have control over these things, have i changed anything by installing the sensors? I would really be more confident that it managed it by itself, and not that i risk messing anything up.

If you can find a ready configuration form some other person with the same machine, then that would of course help. Without one you'll just have to try to detect what sensor is what by yourself. If your machine's BIOS gives you sensor readings, comparing those to lm-sensors values would help. Also it helps to know that if you put the system under full load, the CPU core temperature is the first one to react, pretty much immediately. After that the CPU socket, which should be pretty close to CPU core but lower reaction time to changes in CPU load and usually a bit lower temperature as well. And different ambient/case sensors slowly follow the others.

For fan RPM readings, you'll usually have to either know the designed speeds for the fans or just make a guess based on the fan size and then set the multipliers/dividers in sensors.conf so you get readings that would sound believable for the fan in question.

Different voltages of course would be rather tricky ones. luckily they usually are correct by default. If not, then it's either the same trick of comparing with BIOS values, or bringing out a multimeter and trying to measure them yourself. In the latter case you'd probably just want to ignore the voltage readings or simply trust the defaults to be OK.

The min/max/crit values are not in any way related to the built-in safety features of your hardware. They are simply to tell when lm-sensors should give you a warning about something. So not configuring them properly will not have any effect on your computer shutting itself down in case of overheating, for example, but it might result in programs giving you false warnings. Interestingly the limits tend to be set to rather absurd values by default, even the default values for voltages are nowhere close to ATX specifications, and the temperature values depend on your specific CPU model, case and environment. While one CPU model might be near bursting into flames around 70C, another model can have max temp of 120C and tend to idle around 60C. And "normal" ambient temperatures would be very different based on if you live in tropics or far north like I do.

Finally, if you see any sensor constantly giving insane values, or never changing it's value, you should just disable those readings, it could very well be that there actually aren't any sensors connected to those pins of the sensor chip.

---

### Post by mcduck on 2011-10-13
By the way, 45C doesn't sound that bad at all, considering that it is a laptop. I don't know the spec for E-450, but at least for E-240 and E-350 the max temperature is 90C so it's definitely not close to overheating.

It's pretty much a question of how the cooling of the laptop is configured, it's quite common to allow higher idle temperature to reduce fan noise under low load. I wouldn't make any assumptions based on idle temps, it's only the temperature under continuous load that tells you if the cooling is working properly or not.

(For example on my laptop the idle temperature is usually around 55-60C, and the fan only starts spinning when the temperature reaches 65C. After that even weeks of constant 3D rendering under 100% load won't get the temperature to rise above 70C, which is still 30 degrees under the max temp for the processor. So the manufacturer has clearly just adjusted the fan operation to keep the laptop quiet as long as possible)

---

### Post by moteprime on 2011-10-13
@mcduck

Thanks for giving such a long and good answer.
For a moment I got a little nervous that a was toasting my new laptop.. ;-)

I tried booting in win7 and installed some random core temperature monitor program. It was reading 55-58C.
Back in Ubuntu i tried running Geekbench 3 times in a row, and it quickly ran up to between 58-61C.
So Windows using 30-40% CPU just too keep standing up make that plausible.
And also, i believe that you are right about the different sensors. The single one are always just at little bit higher than one of the two virtual ones. so it must be the CPU and something very close by. The last of the two virtual one are always steady at around -10C from the CPU. But does not go up and down so fast when the CPU sensor do.

Again, thank you for taking your time. I learned a lot to day.
Have a good day.

---

### Post by dcstar on 2011-10-15
> **moteprime said:**
> 
.........
But what is that, Virtual Device and PCI adapter?
I'm using a Lenovo S205, AMD fusion E-450 APU.

Be aware than brand new CPUs are not going to be fully supported by the lm-sensors package - especially old versions.

The E-450 may send the same output as earlier versions of the same family - but it may not (I have had this issue with AMD CPUs previously when they changed the chip family but not the generic CPU name).

You may need to manually install a later version of lm-sensors that supports that CPU.

---

### Post by mcduck on 2011-10-15
E-450 uses the same Zacate core as the E-240 and E-350 I referred to.

The only difference is the GPU part, E-450 has a HD6320 while the others have HD6310. (and of course different multipliers on different models, and only one enabled core on E-250)

---

### Post by moteprime on 2011-10-15
Thanks again.
I will keep looking for somebody smarter than me that put together a setup for a e-450 or maybe E-350. ;-)
But i do believe that the temperatures that the sensors give are reliable.

---

### Post by hramrach on 2011-12-14
Hello,

I am not sure how the sensors are constructed on k10 CPUs so not sure how reliable the reading is. 

Obviously, depending on the sensor construction it might be difficult to tell what a number read from it actually represents. 

(eg. on Intel the reading is distance from Tmax and if you know Tmax you can tell what actual temperature the CPU has but the distance from limit is always correct, some generic sensor chips give number dependent on the termistor attached to them, etc.)

Both my BIOS and the linux k10temp driver agree that Tmax for E-450 is 70 deg C.

Indeed, in the range 70-80 deg which should still be passable but not recommended the board kind of evaporates some plasticky smelling stuff.

At 90 deg C the CPU should shut down which I did not test.

If your sensors don't show any temperature over 60 deg you should be fine.

---

### Post by moteprime on 2011-12-14
Thanks. I never seen it above 60 for more than a few seconds.

---

