---
title: "temperature monitor"
date: 2012-09-01
forum: General Help
---

### Post by cannon_dt on 2012-09-01
Hi,
I just upgrade to 12.04 and I intend to overlock and unlock my phenom ii x2 550 BE. For this I need to monitor temps.
Right now I did lm-sensors, sensors-detect and sensors. I also got gkrellm installed. But I need help understanding the output.

out put of sensors is:
```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.31 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.31 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.02 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.22 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     5578 RPM  (min =  600 RPM)
CHASSIS FAN Speed: 1178 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +45.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +45.0°C  (high = +45.0°C, crit = +75.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +42.2°C  (high = +70.0°C)
                       (crit = +99.5°C, hyst = +97.5°C)
```

Now what is this k10temp-pci-003? Should I even bother about it.

Also I just installed a hd radeon 6670 gaphics card, how do I get to see its temperature. I know amdconfig --odgt gives it but is it possible for me to get it along woth gkrellm output because monitoring would be easier that way.

Outut for sensors detects is:
```
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No
```

then
```

Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.
```

and finally

```
Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8712F Super IO Sensors' (confidence: 9)

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

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
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

```

After that the foll:

```
service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.106" (uid=1000 pid=2881 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

Please help me understand my output.

Ananth

---

### Post by 2F4U on 2012-09-01
```
modinfo k10temp
filename:       /usr/lib/modules/3.5.3-1-ARCH/kernel/drivers/hwmon/k10temp.ko.gz
license:        GPL
author:         Clemens Ladisch <clemens@ladisch.de>
description:    AMD Family 10h+ CPU core temperature monitor
alias:          pci:v00001022d00001403sv*sd*bc*sc*i*
alias:          pci:v00001022d00001603sv*sd*bc*sc*i*
alias:          pci:v00001022d00001703sv*sd*bc*sc*i*
alias:          pci:v00001022d00001303sv*sd*bc*sc*i*
alias:          pci:v00001022d00001203sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.3-1-ARCH SMP preempt mod_unload modversions 
parm:           force:force loading on processors with erratum 319 (bool)

```

Your output may look a bit different, but in general k10temp is the CPU temperature monitoring module.

---

### Post by cannon_dt on 2012-09-01
What is the difference then between that and the CPU temperature reported under the ACPI interface heading? There is a difference there and it worries me.

Also any help on the GPU temp monitoring?

---

### Post by cannon_dt on 2012-09-01
Can someone please help? What temp should I take into consideration while I monitor temps while overclocking?

I need this info badly to get started.

---

### Post by MutantJohn on 2012-09-01
I use Psensor and it displays pretty much everything. And as for the spectrum of allowed temperatures for your individual components, I think you have to check the manufacturer's website.

---

### Post by cannon_dt on 2012-09-01
@Mutant_John
My question is to what temp to consider.
If you see my first output there is a CPU temperature at 45 whereas there is a temp1 at 42. As per 2F4U the temp1 is also CPU temp.
In this the difference is 3 but I have seen it go to 10.
While overclocking it is some important to keep tabs on the temp, so I want to know which one to monitor.

---

### Post by ratcheer on 2012-09-01
Did you get your question about the graphics card answered? It depends on what driver you're using. If you're running the fglrx proprietary driver:

aticonfig --odgt

If you're running the open source radeon driver, I think it just comes with the sensors output.

Tim

---

### Post by cannon_dt on 2012-09-01
@ratcheer
I mentioned aticonfig or amdconfig --odgt in my original post. I know that I can get it off a terminal.
But I was hoping for it to be integrated with my gkrellm so that monitoring with overclocking would be a lot easier, I did not get any info on that.
Even that is secondary now - my primary concern is the diff in temps and which one to consider while overclocking

---

