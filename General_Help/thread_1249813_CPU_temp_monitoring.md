---
title: "CPU temp monitoring"
date: 2009-08-25
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-08-25
I am trying to use "sensors" but am having no luck. I'v Took all steps for installing but not having much luck. 

k-dawg@k-dawg-desktop:~$ sudo sensors-detect
[sudo] password for k-dawg: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801EB ICH5

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): YES
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): YES
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: SMBus I801 adapter at efe0 (i2c-3)
Do you want to scan it? (YES/no/selectively): YES
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
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x6701
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
k-dawg@k-dawg-desktop:~$ 



k-dawg@k-dawg-desktop:~$ sudo /etc/init.d/module-init-tools
[sudo] password for k-dawg: 
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
k-dawg@k-dawg-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
k-dawg@k-dawg-desktop:~$ acpi -V
     Cooling 0: Processor 0 of 0
     Cooling 1: Processor 0 of 0

And When I add to menu bar all I get is what looks to be 2 maxtor hdd's and tepm's, and all I have is one installed on this system. Also, when I open x sensors from the menu It opens a window, but no info at all just an empty window.

---

### Post by dcstar on 2009-08-26
> **Feelin_froggy8877 said:**
> I am trying to use "sensors" but am having no luck. I'v Took all steps for installing but not having much luck. 

k-dawg@k-dawg-desktop:~$ sudo sensors-detect
[sudo] password for k-dawg: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)
...........
[B]Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported.[/B] See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
k-dawg@k-dawg-desktop:~$ 



k-dawg@k-dawg-desktop:~$ sudo /etc/init.d/module-init-tools
[sudo] password for k-dawg: 
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
k-dawg@k-dawg-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
k-dawg@k-dawg-desktop:~$ acpi -V
     Cooling 0: Processor 0 of 0
     Cooling 1: Processor 0 of 0

And When I add to menu bar all I get is what looks to be 2 maxtor hdd's and tepm's, and all I have is one installed on this system. Also, when I open x sensors from the menu It opens a window, but no info at all just an empty window.

As it says, the software cannot detect anything of use in your hardware. You may have to wait for a newer version of Ubuntu (actually the Linux kernel) that supports your hardware in this area.

---

### Post by Feelin_froggy8877 on 2009-08-26
Is there possibly another distro that might? And when I read that at first I figured it meant that my system (mobo, cpu etc) did not support it.

---

### Post by XCan on 2009-08-26
Which mobo and CPU do you have? If you install another distro, it may come with a newer version of lm-sensors that could have drivers for your hardware. Other than that, it won't matter which distro you have. Or you could check the lm-sensors' homepage and see if they have added any support since the version you currently have.

---

### Post by Feelin_froggy8877 on 2009-08-26
Dell Optiplex GX270  Pentium 4 2.40ghz. The reason I started all this was from a recommendation to run a memtest, due to nexuiz always crashing on me (witch just started happening) When I started the memtest from the ubuntu live cd it ran for about ten seconds, than the comp cut off. When I restarted, It said the last shutdown was due to a thermal event, also befor it shutdown on me I seen  a red flag in the lower section on the beginning results. Could that red flag possibly be due to the result of the comp over heating/shutting down?

---

### Post by Feelin_froggy8877 on 2009-08-26
Well I went to the lm-sensors page, as directed from the readout of "sensors-detect" but not quite sure what to do. THeres supposed to be a newer version here...[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices), the link "you should try the latest version of sensors-detect" takes me here...[http://dl.lm-sensors.org/lm-sensors/files/sensors-detect](http://dl.lm-sensors.org/lm-sensors/files/sensors-detect). Am I supposed to copy that script to somwhere? (edit) O.K I am now trying to compile the 3.1.1 version but i'm getting an error...

k-dawg@k-dawg-desktop:~/lm_sensors-3.1.1$ make
gcc -Wl,-rpath,/usr/local/lib -o prog/sensors/sensors prog/sensors/main.ro prog/sensors/chips.ro  -Llib -lsensors
lib/libsensors.so: undefined reference to `sensors_yylex'
lib/libsensors.so: undefined reference to `sensors_lex_error'
lib/libsensors.so: undefined reference to `sensors_yylineno'
lib/libsensors.so: undefined reference to `sensors_scanner_exit'
lib/libsensors.so: undefined reference to `sensors_scanner_init'
lib/libsensors.so: undefined reference to `sensors_yyfilename'
collect2: ld returned 1 exit status
make: *** [prog/sensors/sensors] Error 1

---

### Post by Feelin_froggy8877 on 2009-08-27
O.k after some searching I found "make clean" took care of the compiling error. But still cant get sensors to work. I've heard conky will display temp's on machines that did not support lm-sensors?

---

### Post by XCan on 2009-08-27
I believe conky is just an app that diplays outputs from other apps. There may be some other temp apps out there that can show your temperature. However, merely installing conky alone won't, unfortunately, get you any closer to display your temperatures. :(

---

### Post by Feelin_froggy8877 on 2009-08-28
Whats the differance between using acpi or lm-sensors? For some reason I cant get lm-sensors to work. I been running in circles trying to figure this out.

---

