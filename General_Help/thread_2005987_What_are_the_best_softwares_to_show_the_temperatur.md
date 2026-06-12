---
title: "What are the best softwares to show the temperatures of my hardware?"
date: 2012-06-18
forum: General Help
---

### Post by xp15 on 2012-06-18
I've tried some but it seems that every software thinks the teperature is different.

I would like to get all of your suggestion.

Thanks!

---

### Post by dcottingham on 2012-06-18
That's odd. How different? I mean, are we talking a degree different, or something substantial? And what pieces of software were giving you these different numbers?

---

### Post by xp15 on 2012-06-18
> **dcottingham said:**
> That's odd. How different? I mean, are we talking a degree different, or something substantial? And what pieces of software were giving you these different numbers?

not exactly different, the command software (lmsensor i think), showed three temperatures and thay all were 100 C. So I understood i may need another programs.

what do you offer to me? or maybe you know why I got wrong temperatures?

Thanks

---

### Post by 3Miro on 2012-06-18
Hardware comes with sensors and the Linux kernel has drivers to read off of those sensors. Lm-sensors interfaces with the kernel and it displays the information gathered from the kernel. Any program for reading temperature would go hardware -> kernel -> lm_sensors on any Linux distribution.

If you want a graphical interface, you can try psensor which has very nice Unity integration so you can see pick a temperature and see it on the Unity bar.

On that note, 100C is WAY TOO HIGH. At best, there is a bug in the kernel and this is not the real temperature of your hardware. At worse, the kernel is right and there is something wrong with your laptop. 

- At 100C you should be able to feel your laptop being too hot to touch. Try touching your laptop to see if it is too hot to handle, but be careful, 100C is boiling water temperature and it can leave burns and scars.
- When was the last time you cleaned your laptop from dust?
- Is your laptop fan working?
- What is the temperature of the room where you are using your laptop?
- What is the idle temperature vs the temperature under load?
- Do you have a dual-boot with Windows, where you can use different software to compare the readings. If there is a bug in the Linux kernel, it may not appear on other Linux distributions, so you can also try other Linux or Ubuntu versions to compare readings.

---

### Post by Mark Phelps on 2012-06-18
> **xp15 said:**
> not exactly different, the command software (lmsensor i think), showed three temperatures and thay all were 100 C. So I understood i may need another programs.

what do you offer to me? or maybe you know why I got wrong temperatures?

Thanks

You should go into the BIOS settings for your laptop and see what temps are reported there.  If those also say the same, your laptop is seriously overheating.

---

### Post by dcottingham on 2012-06-18
Yeah, 100 C sounds way too hot, but it also sounds like a suspiciously round number, like something is just not working. I would try looking in /proc/acpi/thermal_zone. There should be one or more directories in there -- on my machine there's just one named "THM". Each of those directories contains, among other things, a "file" named temperature. If you cat it, it tells you the temperature -- like this:

cat /proc/acpi/thermal_zone/THM/temperature

That should show you the temperature, in a direct interface from the kernel driver that's reading the temperature. If that says 100 C, I'd suspect that there's something wrong with your BIOS ACPI, or with the acpi kernel driver.

---

### Post by xp15 on 2012-06-19
> **dcottingham said:**
> Yeah, 100 C sounds way too hot, but it also sounds like a suspiciously round number, like something is just not working. I would try looking in /proc/acpi/thermal_zone. There should be one or more directories in there -- on my machine there's just one named "THM". Each of those directories contains, among other things, a "file" named temperature. If you cat it, it tells you the temperature -- like this:

cat /proc/acpi/thermal_zone/THM/temperature

That should show you the temperature, in a direct interface from the kernel driver that's reading the temperature. If that says 100 C, I'd suspect that there's something wrong with your BIOS ACPI, or with the acpi kernel driver.

I have no "thermal_zone" in acpi folder. there are only 2 empty folders there. but i don't thing that there sensors would tell 100C and my laptop will be feel fine.

---

### Post by Bobhuber on 2012-06-19
> **xp15 said:**
> I've tried some but it seems that every software thinks the teperature is different.

I would like to get all of your suggestion.

Thanks!
Open a terminal and post the output of  # sensors

---

### Post by xp15 on 2012-06-19
> **Bobhuber said:**
> Open a terminal and post the output of  # sensors

```

ubuntu@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1: +0.0°C (crit = +100.0°C)
temp2: +0.0°C (crit = +100.0°C)
temp3: +0.0°C (crit = +100.0°C) 

```I can see now that actually it show 0.

also here a picture prom psensor:
[IMG]http://up354.siz.co.il/up1/bwt4ennmzzlm.png[/IMG]

---

### Post by FFurriouSS on 2012-06-19
I use PSensor it's been great

---

### Post by xp15 on 2012-06-19
> **FFurriouSS said:**
> I use PSensor it's been great

its really a nice program-but it doesn't want to run well on this laptop.
you can see in the picture i've posted.

---

### Post by 3Miro on 2012-06-19
Your temperatures are not 100C, 100C is the "critical" value that is considered too high. You can adjust your laptop to shutdown should it reach critical temperature, which will prevent damage.

In actuality, you are not getting any reading from any sensors. Run the following command:
```
sudo sensors-detect
```
this will look for available sensors. If you still get no reading afterwards, it will be due to bad sensors or kernel bug.

---

### Post by xp15 on 2012-06-19
> **3Miro said:**
> Your temperatures are not 100C, 100C is the "critical" value that is considered too high. You can adjust your laptop to shutdown should it reach critical temperature, which will prevent damage.

In actuality, you are not getting any reading from any sensors. Run the following command:
```
sudo sensors-detect
```this will look for available sensors. If you still get no reading afterwards, it will be due to bad sensors or kernel bug.

Well, here is the output a bit long, but I colored any line that asked me Yes or No.
I answered all question yes. here the output:
```

[B]ubuntu@ubuntu:~$ sudo sensors-detect
    # sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
    # System: Dell Inc. Studio 1537 (laptop)
    # Board: Dell Inc. 0P171H


    This program will help you determine which kernel modules you need
    to load to use lm_sensors most effectively. It is generally safe
    and recommended to accept the default answers to all questions,
    unless you know what you're doing.


    Some south bridges, CPUs or memory controllers contain embedded sensors.
    [COLOR=Purple]Do you want to scan for them? This is totally safe. (YES/no): y[/COLOR]
    Module cpuid loaded successfully.
    Silicon Integrated Systems SIS5595... No
    VIA VT82C686 Integrated Sensors... No
    VIA VT8231 Integrated Sensors... No
    AMD K8 thermal sensors... No
    AMD Family 10h thermal sensors... No
    AMD Family 11h thermal sensors... No
    AMD Family 12h and 14h thermal sensors... No
    AMD Family 15h thermal sensors... No
    AMD Family 15h power sensors... No
    Intel digital thermal sensor... Success!
    (driver `coretemp')
    Intel AMB FB-DIMM thermal sensor... No
    VIA C7 thermal sensor... No
    VIA Nano thermal sensor... No


    Some Super I/O chips contain embedded sensors. We have to write to
    standard I/O ports to probe them. This is usually safe.
    [COLOR=Purple]Do you want to scan for Super I/O sensors? (YES/no): y[/COLOR]
    Probing for Super-I/O at 0x2e/0x2f
    Trying family `National Semiconductor/ITE'... No
    Trying family `SMSC'... No
    Trying family `VIA/Winbond/Nuvoton/Fintek'... No
    Trying family `ITE'... No
    Probing for Super-I/O at 0x4e/0x4f
    Trying family `National Semiconductor/ITE'... Yes
    Found `ITE IT8512E/F/G Super IO'
    (but not activated)


    Some hardware monitoring chips are accessible through the ISA I/O ports.
    We have to write to arbitrary I/O ports to probe them. This is usually
    safe though. Yes, you do have ISA I/O ports even if you do not have any
[COLOR=Purple]    ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y[/COLOR]
    Probing for `National Semiconductor LM78' at 0x290... No
    Probing for `National Semiconductor LM79' at 0x290... No
    Probing for `Winbond W83781D' at 0x290... No
    Probing for `Winbond W83782D' at 0x290... No


    Lastly, we can probe the I2C/SMBus adapters for connected hardware
    monitoring devices. This is the most risky part, and while it works
    reasonably well on most systems, it has been reported to cause trouble
    on some systems.
[COLOR=Purple]    Do you want to probe the I2C/SMBus adapters now? (YES/no): y[/COLOR]
    Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9
    Module i2c-i801 loaded successfully.
    Module i2c-dev loaded successfully.


    Next adapter: Radeon i2c bit bus 0x90 (i2c-0)
[COLOR=Purple]    Do you want to scan it? (YES/no/selectively): y[/COLOR]
    Client found at address 0x28
    Probing for `National Semiconductor LM78'... No
    Probing for `National Semiconductor LM79'... No
    Probing for `National Semiconductor LM80'... No
    Probing for `Winbond W83781D'... No
    Probing for `Winbond W83782D'... No
    Probing for `Winbond W83627HF'... No
    Probing for `Winbond W83627EHF'... No
    Probing for `Winbond W83627DHG/W83667HG/W83677HG'... No
    Probing for `Asus AS99127F (rev.1)'... No
    Probing for `Asus AS99127F (rev.2)'... No
    Probing for `Asus ASB100 Bach'... No
    Probing for `Analog Devices ADM1029'... No
    Probing for `ITE IT8712F'... No
    Client found at address 0x50
    Probing for `Analog Devices ADM1033'... No
    Probing for `Analog Devices ADM1034'... No
    Probing for `SPD EEPROM'... No
    Probing for `EDID EEPROM'... Yes
    (confidence 8, not a hardware monitoring chip)


    Next adapter: Radeon i2c bit bus 0x91 (i2c-1)
[COLOR=Purple]    Do you want to scan it? (YES/no/selectively): y[/COLOR]


    Next adapter: Radeon i2c bit bus 0x92 (i2c-2)
[COLOR=Purple]    Do you want to scan it? (YES/no/selectively): y[/COLOR]


    Next adapter: Radeon i2c bit bus 0x93 (i2c-3)
[COLOR=Purple]    Do you want to scan it? (YES/no/selectively): y[/COLOR]


    Next adapter: Radeon i2c bit bus 0x14 (i2c-4)
[COLOR=Purple]    Do you want to scan it? (YES/no/selectively): y[/COLOR]
    y


    Now follows a summary of the probes I have just done.
    Just press ENTER to continue:
    Driver `coretemp':
    * Chip `Intel digital thermal sensor' (confidence: 9)


    To load everything that is needed, add this to /etc/modules:
    #----cut here----
    # Chip drivers
    coretemp
    #----cut here----
    If you have some drivers built into your kernel, the list above will
    contain too many modules. Skip the appropriate ones!


[COLOR=Purple]    Do you want to add these lines automatically to /etc/modules? (yes/NO)y[/COLOR]
    Successful!


    Monitoring programs won't work until the needed modules are
    loaded. You may want to run 'service module-init-tools start'
    to load them.


    Unloading i2c-dev... OK
    Unloading i2c-i801... OK
    Unloading cpuid... OK 

[/B]

```

---

### Post by 3Miro on 2012-06-19
Now you can either type:
```

sudo service module-init-tools start
sensors

```
or you can reboot and try
```

sensors

```
again.

---

### Post by xp15 on 2012-06-20
> **3Miro said:**
> Now you can either type:
```

sudo service module-init-tools start
sensors

```or you can reboot and try
```

sensors

```again.

I run the first two commands. that is the output now, but seems to miss some other important information from other sensors:
```

ubuntu@ubuntu:~$ sudo service module-init-tools start
module-init-tools stop/waiting
ubuntu@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1: +0.0°C (crit = +100.0°C)
temp2: +0.0°C (crit = +100.0°C)
temp3: +0.0°C (crit = +100.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0: +32.0°C (high = +105.0°C, crit = +105.0°C)
Core 1: +30.0°C (high = +105.0°C, crit = +105.0°C)

```

and Thanks you for helping me.

---

### Post by 3Miro on 2012-06-20
The ACPI is giving you some bug, my guess is that this is due to many laptops not following the ACPI standards. Anyway, you are reading 32C for your CPU, which is perfectly normal and healthy temperature.

Psensors should get this reading now and you can have it run in the Unity panel to keep an eye on it.

---

### Post by xp15 on 2012-06-21
> **3Miro said:**
> The ACPI is giving you some bug, my guess is that this is due to many laptops not following the ACPI standards. Anyway, you are reading 32C for your CPU, which is perfectly normal and healthy temperature.

Psensors should get this reading now and you can have it run in the Unity panel to keep an eye on it.

at first I got core1 and 2 temp', then the computer has shutdown again and after that i got more data from more sensors:
```

ubuntu@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +46.0°C  (crit = +100.0°C)
temp2:        +46.0°C  (crit = +100.0°C)
temp3:        +65.0°C  (crit = +100.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +42.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +42.0°C  (high = +105.0°C, crit = +105.0°C)

```

and in Psensor:
[IMG]http://up354.siz.co.il/up2/2y2eejwqz0mg.png[/IMG]


so, it seems the temp' is causing the shutings-down. but is there a way so i will be able to know which hardware component is belong to each temp' instead of temp1,2,3... ?

Thank for your help (:

---

