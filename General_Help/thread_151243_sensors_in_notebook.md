---
title: "sensors in notebook"
date: 2006-03-27
forum: General Help
---

### Post by mitjab on 2006-03-27
is it possible that notebook has no sensors for temperature?
I can't find any sensor with lm_sensors.

---

### Post by John.Michael.Kane on 2006-03-27
mitjab yes some notebooks do not have fan or temp sensors. my averatec notebook being one of those that don't.

---

### Post by mitjab on 2006-03-27
In windows everest home edition show me temp for proc and hdd but lm_sensors doesn't find anything.

---

### Post by John.Michael.Kane on 2006-03-27
You mind listing your laptop brand, and cpu ect.


thanks

---

### Post by mitjab on 2006-03-27
```
You mind listing your laptop brand, and cpu ect.
```

how?

---

### Post by John.Michael.Kane on 2006-03-27
[QUOTE=mitjab]```
You mind listing your laptop brand, and cpu ect.
```

how?[/QUOTE]

Just telling me what brand it is, and what cpu is in it. is a good start.

---

### Post by mitjab on 2006-03-27
gericom ego 1780 with centrino 1.7 proc in it.

---

### Post by John.Michael.Kane on 2006-03-27
Have a look over this. it may help.
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors)

---

### Post by mitjab on 2006-03-27
yes i work with this howto

```
mitjab@ubuntu:~$ sudo sensors-detect
Password:

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): yes
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (0x61)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0x61)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0x61)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0x61)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0x61)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0x61)
Probing for `Winbond W83L517D Super IO'
  Success... (no hardware monitoring capabilities)
Probing for `Winbond W83627EHF Super IO Sensors'
  Failed! (0x6102)

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
mitjab@ubuntu:~$

```

and no sensor detected

---

### Post by John.Michael.Kane on 2006-03-27
Well that would leave me to beleave that your sensor is not supported right now.

---

