---
title: "Fan speed / fan throttle / fan always on"
date: 2010-05-31
forum: General Help
---

### Post by erikmorres on 2010-05-31
Hi,

I'm hoping someone can help me with an issue I have with Ubuntu 10.04 LTS on my new system.

Since my IBM ThinkPad T42 broke down, I've replaced it with a desktop system (HP Slimline s5130nl; Specifications: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01871763&cc=uk&dlc=en&lc=en&jumpid=reg_R1002_UKEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01871763&cc=uk&dlc=en&lc=en&jumpid=reg_R1002_UKEN)). However with this system I've run into a frustrating issue: the fans (at least the CPU fan) run constantly at max speed. Forcing me to switch to Windows Vista :(.

I've searched for solutions on this forum and the internet to no avail.

What I've noticed so far:


[LIST=1]
[*]*/proc/acpi/fan* and */proc/acpi/thermal_zone/* are not (being) populated;
[*]*pwmconfig *finds the sensors and adds these to the modprobe list, however I can't manualy configure the settings; I'm getting an error message that the sensor can't be configured manually therefore I can't load/launch *fancontrol *since it quits with the error message that no configuration file was found;
[*]Although I'm using a HP desktop system, I've tried the *thinkfan *package to no avail;
[*]Tried adding "*acpi_osi*=" with different parameters to GRUB2 to no avail;
[*]*lm-sensors* seems to produce the expected output and thus seems to work correctly.
[/LIST]
Also I've browsed through the BIOS to see if I can find a setting that would have the system automatically control the fan speed, however I've noticed that the BIOS is kind of simple and scarce in features and settings; hence providing no solution.

I'm hoping somebody has an idea or, better yet, a solution :) to resolve this and enable me to get rid of Windows Vista and switch over to Ubuntu again ;)

Thank you in advance!

Kind regards,

Erik

---

### Post by davidmohammed on 2010-05-31
are you using acpi=off or any other options other than quiet splash in your grub settings?

---

### Post by davidmohammed on 2010-05-31
... what acpi_osi= options have you tried?

acpi_osi="!Windows 2006"
acpi_osi="Windows 2006"
acpi_osi="Linux"
acpi_osi="Windows 2001 SP2"

possibly your HP is affected by [this]("http://ubuntuforums.org/showthread.php?t=1036051") issue?

---

### Post by erikmorres on 2010-05-31
> **davidmohammed said:**
> ... what acpi_osi= options have you tried?


I've tried *acpi_osi="Linux"* and *acpi=force*. Also when I stumbled upon this, I had only Ubuntu installed i.e. no dual boot.

Do note that I have no issue booting Ubuntu and/or thermal issues. For example when I boot with the Ubuntu LiveCD, the fan(s) in the system will run full throttle. If I then reboot into Windows Vista, the fan(s) throttle down immediately. Another thing I noticed is that when I boot with a Symantec Ghost CD or the recovery solution from HP, the fan(s) also run full throttle, suggesting to me that the fan requires some sort of driver or at least needs to be actively managed.

I'll try to check on the DSDT issue with the Ubuntu LiveCD since I had to remove Ubuntu to restore Windows Vista.

---

### Post by erikmorres on 2010-05-31
> **erikmorres said:**
> I'll try to check on the DSDT issue with the Ubuntu LiveCD since I had to remove Ubuntu to restore Windows Vista.

While I was reading the HOWTO, I noticed the following comment:

> **67GTA said:**
> 
[COLOR=Red]UPDATE:[/COLOR] The kernel dev's will no longer use the  patch to enable custom DSDT files for Karmic 9.10 and beyond. Jaunty  9.04 is the last version this will work on. You are urged to file a bug  report for DSDT errors.

I assume this implicates that you cannot update or change the DSDT in Lucid Lynx 10.04 LTS anymore.

Is there another way to tackle this issue? Also is there a way I can share output - e.g. error messages regarding ACPI/DSDT - with Ubuntu developers in order to help improve Ubuntu?

---

### Post by davidmohammed on 2010-05-31
how did you get go trying the other acpi_os values? 
It seems that thread is actively being answered by the originator - so you still can find out if you've got a buggy dsdt

Also - this [thread]("http://ubuntuforums.org/showthread.php?t=1341580") shows you how to compile back-in the custom dsdt support for lucid.

---

### Post by erikmorres on 2010-05-31
> **davidmohammed said:**
> how did you get go trying the other acpi_os values? 


I had Ubuntu installed and tried to resolve the issue this weekend, however since the noise of the fan was driving me crazy so I opted to remove Ubuntu and reinstall Vista.

> **davidmohammed said:**
> 
It seems that thread is actively being answered by the originator - so you still can find out if you've got a buggy dsdt

Also - this [thread]("http://ubuntuforums.org/showthread.php?t=1341580") shows you how to compile back-in the custom dsdt support for lucid.

Thanks for your active support!

I also found a link in the article you are referring to ([http://web.archive.org/web/20080125015702/http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://web.archive.org/web/20080125015702/http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)). Which states: *"If your DSDT is buggy, then you'll see some errors and/or warnings when  you recompile."*, so I guess I can conveniently use the LiveCD to check if the DSDT is the true issue before going through the hassle of removing Vista and reinstalling Ubuntu.

---

### Post by erikmorres on 2010-06-01
I checked the DSDT file, however recompiling it without any changes (only) produces a couple of warnings:

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   132:         Name (_T_0, Zero)
Remark   5110 -                  ^ Use of compiler reserved name (_T_0)

dsdt.dsl  5223:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5237:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5252:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5267:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5281:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5296:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5311:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

ASL Input:  dsdt.dsl - 6150 lines, 190558 bytes, 2724 keywords
AML Output: dsdt.aml - 22355 bytes, 729 named objects, 1995 executable opcodes

Compilation complete. 0 Errors, 7 Warnings, 1 Remarks, 66 Optimizations

```Also I checked the acpi_osi switches I didn't previously check, however to no avail. Next to that I did notice that Ubuntu correctly detects RPM of the fans as well as the temperature of the systems components. Could this be a clue that the solution lies in configuring something and/or start a daemon to monitor this?

Sensors output:

```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +40.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +28.0°C  (high = +74.0°C, crit = +100.0°C)  

f8000-isa-0a00
Adapter: ISA adapter
+3.3V:       +3.38 V
3VSB:        +3.39 V
Vbat:        +3.30 V
fan1:       1507 RPM
fan2:        831 RPM
fan3:          0 RPM  ALARM
fan4:          0 RPM
temp1:       +38.0°C  (high = +70.0°C, hyst = +60.0°C)  
temp2:       +34.0°C  (high = +100.0°C, hyst = +85.0°C)  sensor = Intel PECI
temp3:       +36.0°C  (high = +100.0°C, hyst = +85.0°C)
```

I'm really hoping somebody has a solution for this, since I am really missing working on Ubuntu. I'll also check with the DSDT-thread.

Thank you in advance!

---

### Post by davidmohammed on 2010-06-01
Hi there,
  two more tries from my end - may be a stab in the dark - suggest you install the [latest .34 kernel]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") to see if your issue is specific to the lucid kernel or also exists upstream in the latest kernels.

This [link]("http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/") may be desperate - but worth a read.

---

### Post by erikmorres on 2010-06-18
David,

Thank you very much for your support! I am sorry to say that I have been unable to get this issue fixed and - after a lot of frustration - decided to purchase and install a copy of Windows 7. Although I'd really would have liked to switch to Linux, I guess its still a work in progress and not ready for the mainstream user like myself.

I might check on Ubuntu 10.10 to see if the issues with the fan/ACPI have been resolved. However for now I'll stick with Windows 7 - even if it was only because otherwise it would be a waste of my $199,- costing copy of Windows 7 :).

KR, Erik

---

### Post by erikmorres on 2010-06-18
David,

Thank you very much for your support! I am sorry to say that I have been unable to get this issue fixed and - after a lot of frustration - decided to purchase and install a copy of Windows 7. Although I'd really would have liked to switch to Linux, I guess its still a work in progress and not ready for the mainstream user like myself.

I might check on Ubuntu 10.10 to see if the issues with the fan/ACPI have been resolved. However for now I'll stick with Windows 7 - even if it was only because otherwise it would be a waste of my $199,- costing copy of Windows 7 :).

KR, Erik

---

### Post by Suicidal State Machine on 2010-06-24
I've been seeing the same issue with the fans going full blast always (even when the system isn't loaded and core temps are low). I think in my case it's more of a hardware limitation than a software issue, the case fans are all three pin type (four pin connectors are needed for the motherboard to control the fan speed). I'd upgrade the fans but my motherboard has mostly three pin connectors too. 

I do have a low tech solution that might also be useful to anyone fighting the same driver issues - just solder a resistor in series with the 12 volt supply to the fan. Or if you feeling lazy (as I was) you can order a few of these: [http://www.mnpctech.com/7volt_Resistor_Computer_Fan_Mod.html](http://www.mnpctech.com/7volt_Resistor_Computer_Fan_Mod.html).

---

### Post by Gordonisnz on 2010-09-30
> **davidmohammed said:**
> ... what acpi_osi= options have you tried?

acpi_osi="!Windows 2006"
acpi_osi="Windows 2006"
acpi_osi="Linux"
acpi_osi="Windows 2001 SP2"

possibly your HP is affected by [this]("http://ubuntuforums.org/showthread.php?t=1036051") issue?


Hello..

which file do I edit / sudo / gedit  to edit the above details...

(pretend i don't know what the above means)

---

### Post by mockingbird on 2010-10-25
You want /etc/default/grub

---

### Post by asus-user on 2011-07-16
Hello all,

I am an asus U33j user, and I have this same problem since I moved from WIN7 to Ubuntu 10.04. and for me it is a very big waste of power during the operation time. 
did anyone tried the next versions of Ubuntu like 10.10 or even 11.04?

I believe that you guys, like me, don't like to get back to Windows after you get rid of it!

Greeings,

---

### Post by asus-user on 2011-07-18
hey, 
I think i found the solution for some types of PCs,  it is a small sys-tray applet called "Eee Applet" and can be installed from the software center.
it gives you the options to control the speed of your fan and adjust it to many options ;)
It works fine on my Asus, try it and tell me what do you think..
Regards,

---

### Post by feistybill on 2011-07-18
AFAIK, the high CPU usage, high temps, fans always on, etc. are due to bugs in older kernels. Can't remember exactly, I used to have the same problems until I compiled and installed the latest kernel.

More info here here:
[http://www.phoronix.com/vr.php?view=16181](http://www.phoronix.com/vr.php?view=16181)
[http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1)

---

