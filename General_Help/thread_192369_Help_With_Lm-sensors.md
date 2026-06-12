---
title: "Help With Lm-sensors"
date: 2006-06-08
forum: General Help
---

### Post by digitalkarabao on 2006-06-08
This is a re-post. Nobody seems to be noticing the thread. :)

lm-sensors is installed but whenever i run sensors-detect and answers yes to the questions..i receive the log below.

i was able to run lm-sensors unser breezy before.

auric@digitalpenguin:~$ su
Password:
root@digitalpenguin:/home/auric# sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:1

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
Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Controller
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-sis96x' already loaded.
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

Next adapter: SiS96x SMBus adapter at 0x0c00
Do you want to scan it? (YES/no/selectively):
Client found at address 0x08
Client found at address 0x10
Client found at address 0x30
Client found at address 0x31
Client at address 0x50 can not be probed - unload all client drivers first!
Client at address 0x51 can not be probed - unload all client drivers first!

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no):
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

Do you want to scan for Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
Failed! (0xea11)
Probing for `ITE 8705F Super IO Sensors'
Failed! (0xea11)
Probing for `ITE 8712F Super IO Sensors'
Failed! (0xea11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87591 Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PC87371 Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PC97371 Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PC8739x Super IO'
Success... (no hardware monitoring capabilities)
Probing for `Nat. Semi. PC8741x Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PCPC87427 Super IO'
Failed! (0xea)
Probing for `SMSC 47B27x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M14x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47S42x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47S45x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M172 Super IO'
Failed! (0xea)
Probing for `SMSC LPC47B397-NC Super IO'
Failed! (0xea)
Probing for `VT1211 Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83627HF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83627THF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83637HF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83687THF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83697HF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83697SF/UF Super IO PWM'
Failed! (0xea)
Probing for `Winbond W83L517D Super IO'
Failed! (0xea)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
Failed! (0xea11)

Do you want to scan for secondary Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
Failed! (0xec11)
Probing for `ITE 8705F Super IO Sensors'
Failed! (0xec11)
Probing for `ITE 8712F Super IO Sensors'
Failed! (0xec11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87591 Super IO'
Success... but not activated
Probing for `Nat. Semi. PC87371 Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PC97371 Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PC8739x Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PC8741x Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PCPC87427 Super IO'
Failed! (0xec)
Probing for `SMSC 47B27x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M14x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47S42x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47S45x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M172 Super IO'
Failed! (0xec)
Probing for `SMSC LPC47B397-NC Super IO'
Failed! (0xec)
Probing for `VT1211 Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83627HF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83627THF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83637HF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83687THF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83697HF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83697SF/UF Super IO PWM'
Failed! (0xec)
Probing for `Winbond W83L517D Super IO'
Failed! (0xec)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
Failed! (0xec11)

Sorry, no chips were detected.
Either your sensors are not supported, or they are
connected to an I2C bus adapter that we do not support.
See doc/FAQ, doc/lm_sensors-FAQ.html, or
[http://www2.lm-sensors.nu/~lm78/cvs/...nsors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/...nsors-FAQ.html)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, see
[http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.

---

### Post by henriquemaia on 2006-06-08
I have the same result as you. But I don't know if this happens because my sensors are not supported.

---

