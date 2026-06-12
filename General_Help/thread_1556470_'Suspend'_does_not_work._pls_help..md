---
title: "'Suspend' does not work. pls help."
date: 2010-08-19
forum: General Help
---

### Post by JustLikeYouImagined on 2010-08-19
I have a HP Pavillian Laptop. Intel Core 2 Duo @ 2 GHz. 4 GB RAM.

My  laptop doesn't go into sleep mode when I'm running ubuntu. The  screen  goes off, but the system is still running. I mean you can hear  the fan  and everything. The sleep in Windows Vista is quite convenient.  I just  press a button, close the lid and I can later resume from where  I left  it. While in the sleep mode, the laptop appears to be "off".  There's  just one small light that keeps blinking.

I've tried the  hibernate in ubuntu. But that isn't satisfactory either.  First of all,  it takes forever to come out of the hibernate state.  Secondly, it  doesn't preserve the application state. For example, if  I'm watching 45  minute flash video on google video. I have the entire  video buffered.  After watching half the video, I need to step out for a  little while. I  do the hibernate. After coming back, I can't resume  watching from where I  left it. I have to reload the video. This doesn't  happen in the Vista  sleep mode.

What is the solution to this? Please help

BTW, I have installed the 64 bit version (of ubuntu 10.04)

---

### Post by silbak04 on 2010-08-20
I would just run this in a terminal ```
$ sudo /etc/acpi/sleepbtn.sh
```

---

### Post by JustLikeYouImagined on 2010-08-20
> **silbak04 said:**
> I would just run this in a terminal ```
$ sudo /etc/acpi/sleepbtn.sh
```
That didn't work either. Like I said before, the screen goes blank but the CPU fan keeps running. If I press a key, the screen comes back on with the unlock prompt.

---

### Post by silbak04 on 2010-08-20
Did you try messing in the BIOS...sometimes this can be an issue in the BIOS...I'll keep looking for solutions.

---

### Post by silbak04 on 2010-08-20
Also try taking it apart and cleaning out all the dust, see if that works as well...

---

### Post by silbak04 on 2010-08-20
also install lm-sensors and then run ```
$ sudo sensors detect
cat /proc/acpi/thermal_zone/THRM/temperature
``` read me your output

---

### Post by silbak04 on 2010-08-20
^ Do all that after you check your BIOS settings under power management, and that doesn't help...

---

### Post by supermario641996 on 2010-08-20
If you installed Ubuntu through Wubi, hibernation is not supported.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
READ BELLOW
> Hibernation is not supported under Wubi, moreover Wubi filesystem is  more vulnerable to hard-reboots (turning off the power) and power  outages than a normal filesystem, so try to avoid unplugging the power.  An Ubuntu installation to a dedicated partition provides a filesystem  that is more robust and can better tolerate such events.

---

### Post by JustLikeYouImagined on 2010-08-20
> **silbak04 said:**
> also install lm-sensors and then run ```
$ sudo sensors detect
cat /proc/acpi/thermal_zone/THRM/temperature
``` read me your output
```
ayush@hp-laptop:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
ayush@hp-laptop:~$ sudo sensors detect
Parse error in chip name `detect'
Try `sensors -h' for more information
ayush@hp-laptop:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             42 C
ayush@hp-laptop:~$ 

```

---

### Post by JustLikeYouImagined on 2010-08-20
> **supermario641996 said:**
> If you installed Ubuntu through Wubi, hibernation is not supported.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
READ BELLOW
I'm not running ubuntu through Wubi. Also, hibernate works fine. Suspend doesn't.

---

### Post by JustLikeYouImagined on 2010-08-23
I've tested on ubuntu, linux mint, kubuntu and fedora. Sleep/Suspend doesn't work on any distro.
Should I try debian?

---

