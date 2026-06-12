---
title: "can't use ibm-acpi"
date: 2006-02-21
forum: General Help
---

### Post by bigblop on 2006-02-21
I have the latest kernel for Ubuntu 2.6.12-10-386 installed on an IBM T40/p.

I have this in my /etc/modules:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
acpi_ibm

```

But the fan still makes the same noise.

In the readme file there is a mention of setting something to "experimental=1", but where should I type this? Should I make a Xdefaults file and put it there??

Furtheremore the README file says that it is possible to enable/disable the fan completely by:

	echo enable  >/proc/acpi/ibm/fan
	echo disable >/proc/acpi/ibm/fan

But there is nothing called "fan" in that folder. If I look in /proc/acpi/ instead I find the folder fan:

johs@ubuntu:/proc/acpi$ ls
ac_adapter  dsdt                 fan     power_resource  thermal_zone
alarm       embedded_controller  hotkey  processor       video
battery     event                ibm     sleep           wakeup
button      fadt                 info    sony            wmi
johs@ubuntu:/proc/acpi$

Should I download some script to this folder to make it work??

---

### Post by JELaVallee on 2006-02-21
[QUOTE=bigblop]I have the latest kernel for Ubuntu 2.6.12-10-386 installed on an IBM T40/p.

I have this in my /etc/modules:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
acpi_ibm

```

But the fan still makes the same noise.
[/QUOTE]

Not an expert here... but is the ibm_acpi module being loaded?  And I think that the name of the module you have listed above in /etc/modules is wrong.

Try doing an 'lsmod|grep acpi' and see if that lists the acpi modules.

Also have you checked out this site? [http://www.thinkwiki.org](http://www.thinkwiki.org)

It's a great resource for those with ThinkPads who prefer to run linux.

cheers,
Etienne

---

### Post by z_diver on 2006-02-21
On the funny side, well if you don't work for Intel, Linus offered this advice back in 03. :mrgreen: 

"Modern PCs are horrible. ACPI is a complete design disaster in every way. But we're kind of stuck with it. If any Intel people are listening to this and you had anything to do with ACPI, shoot yourself now, before you reproduce." Linus Torvolds(2003)

---

