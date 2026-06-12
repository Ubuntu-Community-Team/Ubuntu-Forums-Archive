---
title: "Changing fan speed with lm-sensors"
date: 2010-12-06
forum: General Help
---

### Post by jpr0 on 2010-12-06
Hi 

Can someone help me control my cpu fan speed? It's really loud, and I'm not stressing the CPU at all, but it seems to be running at 110% all the time. 

I've tried going through some old posts related to lm-sensors but nothing seems to work. 

I'm using an Asus motherboard (M4A88TD-M), an AMD 1075t six-core processor, and I have Ubuntu 10.10 installed. Ive run sensors-detect, followed the onscreen prompts... the output looks like this: 

```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: System manufacturer System Product Name
# Board: ASUSTeK Computer INC. M4A88TD-M EVO

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): Silicon Integrated Systems SIS5595...                       No
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
Do you want to scan for Super I/O sensors? (YES/no): Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8721
    (logical device 4 has address 0x290, could be sensors)
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
interfaces? (YES/no): Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.
```

I really don't know what to do with this now? 

The output of "sensors" is: 

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +19.5°C  (high = +70.0°C, crit = +99.5°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.21 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.33 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.93 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.03 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3292 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1157 RPM  (min =  600 RPM)
POWER FAN Speed:  1085 RPM  (min =  600 RPM)
CPU Temperature:   +30.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +29.0°C  (high = +45.0°C, crit = +75.0°C)  
```

(It doesn't detect more than one core...). Anyway, I'm just lost now. I'm not entirely sure how to use this information to slow my CPU fan down. If someone could give me a walk-through I'd appreciate it. 

Thanks.

---

### Post by jpr0 on 2010-12-06
Additionally, pwmconfig says this: 

```
sudo pwmconfig 
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

---

### Post by Mark Phelps on 2010-12-07
OK ... so I know you asked about changing the fan speeed ... but my advice is -- DON'T!

The fan is running fast -- for a reason!  It's most likely that the CPU is running hot and the fan is trying to keep it cool.  Slowing down the fan will only burn out your CPU.

A better approach is to (1) figure out why the CPU is running hot (usually because it is running at a higer % utilization than before), (2) cut back on the CPU utilization (which will have the effect of causing the fan to run less often as well).

---

### Post by no2498 on 2010-12-07
open a terminal type htop it tells you how to install it
now type htop watch what is running that should tell you what needs fixed
btw ive seen some say there fan did not run at all
be happy yours is running

---

### Post by fragos on 2010-12-07
If all else fails Zalman has inexpensive fan controls. I chose the Zalman Fanmate 2 Variable Speed Fan Controller. Make sure you're controlling the right fan by running your PC with the cover open and placing your finger on the center of each fan hub to slow or stop it. At one point I had a noisy case fan which I replaced with a quiet ball bearing fan after using a Zalman controller for a while. When I replaced my PS that fan was loud. The PS fan only had two pins so I replaced it with a 3 pin fan powered from an PS connector external to the PS. Still loud so I used my Zalman again. Not all fans that claim to be low noise are.

---

### Post by jpr0 on 2010-12-07
> **Mark Phelps said:**
> OK ... so I know you asked about changing the fan speeed ... but my advice is -- DON'T!

The fan is running fast -- for a reason!  It's most likely that the CPU is running hot and the fan is trying to keep it cool.  Slowing down the fan will only burn out your CPU.

A better approach is to (1) figure out why the CPU is running hot (usually because it is running at a higer % utilization than before), (2) cut back on the CPU utilization (which will have the effect of causing the fan to run less often as well).

Hi, thanks for the response. The fan isn't running at this speed for any reason other than the OS isn't regulating the fan speed. I said in my post that there is nothing stressing the CPU. In fact I built my system yesterday, and had just installed ubuntu. The system was idling. Yet the fans run at full speed regardless of the load on the cpu (at no point in the day yesterday did the cpu fan drop from full speed).

---

### Post by fragos on 2010-12-07
If I'm not mistaken a 4 pin connector is required for computer control of fan speed. Potentiometers can be used with 3 pin connectors.

---

### Post by jpr0 on 2010-12-07
Why do we plug them into the motherboard then, instead of just straight into the PSU?

---

### Post by jpr0 on 2010-12-07
> **Mark Phelps said:**
> OK ... so I know you asked about changing the fan speeed ... but my advice is -- DON'T!

The fan is running fast -- for a reason!  It's most likely that the CPU is running hot and the fan is trying to keep it cool.  Slowing down the fan will only burn out your CPU.

A better approach is to (1) figure out why the CPU is running hot (usually because it is running at a higer % utilization than before), (2) cut back on the CPU utilization (which will have the effect of causing the fan to run less often as well).

I've attached a screenshot from Htop. 
Here is the output from "fancontrol": 

```
fancontrol
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file

```

---

### Post by fragos on 2010-12-07
> **jpr0 said:**
> Why do we plug them into the motherboard then, instead of just straight into the PSU?

I'm inclined to think because that's where the small connectors for fans are located for convenience but you can use an adapter cable to direct connect to the PS if you wish. I believe the 3rd wire is used for measuring but not controlling fan speed and that might have to be on the mobo.

---

### Post by jpr0 on 2010-12-07
> **fragos said:**
> I'm inclined to think because that's where the small connectors for fans are located for convenience but you can use an adapter cable to direct connect to the PS if you wish. I believe the 3rd wire is used for measuring but not controlling fan speed and that might have to be on the mobo.

Right. This is what wiki says too: 

[http://en.wikipedia.org/wiki/Computer_fan](http://en.wikipedia.org/wiki/Computer_fan)

I'll check the connectors on the fans. It might well be that they're only 3 pin. Thanks a lot.

---

### Post by v1ad on 2010-12-07
i'm pretty sure the bios controls the cpu fan. maybe go into to bios, see the cpu temp, if not to high adjust the fan speed for that temp.

---

### Post by Mark Phelps on 2010-12-08
> **jpr0 said:**
> ...The system was idling. Yet the fans run at full speed ...

OK ... that's a different problem.  I understand now why you are trying to slow down the fans.  

Just didn't want you burning out your CPU just to keep the fans quiet!

---

### Post by jpr0 on 2010-12-08
It's okay. I figured it out, as the previous poster noted, it can be controlled in the BIOS. Asus motherboards have a "cool n quiet" feature, which controls the fans according to some profile. It was disabled in the BIOS, so after enabling it now my fan is running nice and quiet :) 

Thanks.

---

