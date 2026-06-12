---
title: "Fan runs constanly!"
date: 2006-02-21
forum: General Help
---

### Post by bigblop on 2006-02-21
I use Ubuntu 5.10 on an IBM T40/P. The fan runs constanly when I run Ubuntu Linux eventhough I only use emacs.

Is there some way to make the fan stop like it does in winXP??

---

### Post by mwallace on 2006-02-21
You should be able to open up a command prompt and just type "laptop mode" and hit enter.  That should enable power managment.  Also try "sudo laptop mode" if you get an error or it doesn't seem to work, but I don't think you need to use sudo/run the command as root.  Hope that helps.  =)

---

### Post by bigblop on 2006-02-21
I already have this running, but it only reduce the noise the harddisk produce, not the noise produced by the fan!

---

### Post by antidrugue on 2006-02-21
Lucky you have a T40, this will work on it:
[http://ibm-acpi.sourceforge.net/](http://ibm-acpi.sourceforge.net/)

...everything has been tested and work on the T40, including fan control.

Since **kernel 2.6.10** it is part of the kernel.

Make sure you have linux-image-2.6.10 or later installed. To make sure:
```

uname -a

```

Then add "acpi_ibm" to /etc/modules and reboot. Or just type 
```

sudo modprobe acpi_ibm

```

---

### Post by bigblop on 2006-02-21
Ok I have a newer kernel. Then I only need to:

sudo modprobe acpi_ibm

should I not download/install the driver from this site first:

[http://ibm-acpi.sourceforge.net/](http://ibm-acpi.sourceforge.net/)

---

### Post by antidrugue on 2006-02-21
Nope, put "acpi_ibm" in /etc/modules.

No need to download anything, because as mentionned [ on the site](http://ibm-acpi.sourceforge.net/) : "The ibm-acpi driver is part of kernel 2.6.10 and later (option CONFIG_ACPI_IBM)."

This option refers to the kernel configuration, so don't bother unless you plan to compile your own kernel -- which by the way is always the best solution for a laptop.

---

### Post by antidrugue on 2006-02-21
As mentionned in [ the README](http://ibm-acpi.sourceforge.net/README):
> 
USE
WITH CAUTION! To use this feature, you need to supply the
experimental=1 parameter when loading the module.

...

The fan may be enabled or disabled with the following commands:

	echo enable  >/proc/acpi/ibm/fan
	echo disable >/proc/acpi/ibm/fan

WARNING WARNING WARNING: do not leave the fan disabled unless you are
monitoring the temperature sensor readings and you are ready to enable
it if necessary to avoid overheating.


---

### Post by bigblop on 2006-02-21
Ok so I already have what can be downloaded from the site, right?
when I do "locate acpi_ibm ", I don't get anything...

You write that I should put acpi_ibm in /etc/modules, which  currently looks like this:


```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

```

I would then change it to:

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


would doing this manually be the same as:

sudo modprobe acpi_ibm

??


Do I need to put: option CONFIG_ACPI_IBM somewhere?

after I reboot, will the fan adjust automatically or do I need to do additional configurations?

---

### Post by bigblop on 2006-02-21
You write:


 USE
WITH CAUTION! To use this feature, you need to supply the
experimental=1 parameter when loading the module.


I don't understand should I change my /etc/modules to:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
acpi_ibm experimental=1

```
??

currently I just have 

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

and it seems to work fine, I am not sure I would like to experiment

---

### Post by antidrugue on 2006-02-21
[QUOTE=bigblop]
Do I need to put: option CONFIG_ACPI_IBM somewhere?
[/QUOTE]

This line goes in the config file you compile your own kernel... i guess you don't want to do that.

The answer to all your questions should be somewhere in there:
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by bigblop on 2006-02-21
do I need this:

acpi_ibm experimental=1

or is that only if I dare to risk the life of my CPU?

---

### Post by antidrugue on 2006-02-21
Mouhaha...

Well... I'm sure under 100 celcius your cpu will survive...

Then again I try to keep mine under 50 celcius (hardware will last longer).

Take a look at this, it seems right for you:
[http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script)

And more importantly this:
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

---

### Post by bigblop on 2006-02-21
I dont't get it. I thought it would work without having to install some of the scripts that you linked to.

Eventhough I now have this in my modules file:

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

Only cold air comes out of the fan (I have rebooted the machine).

I still don't understand what they mean by "experimental=1". Where should I type this and what happens?

In the readme file it says:

	echo enable  >/proc/acpi/ibm/fan
	echo disable >/proc/acpi/ibm/fan

but I don't have anything called fan in the ibm folder:

johs@ubuntu:/proc/acpi/ibm$ ls
bay  bluetooth  dock  driver  hotkey  light  video
johs@ubuntu:/proc/acpi/ibm$


its in this folder (/proc/acpi/):

johs@ubuntu:/proc/acpi$ ls
ac_adapter  dsdt                 fan     power_resource  thermal_zone
alarm       embedded_controller  hotkey  processor       video
battery     event                ibm     sleep           wakeup
button      fadt                 info    sony            wmi
johs@ubuntu:/proc/acpi$


is it a typo in the README file?

---

### Post by antidrugue on 2006-02-21
Well it seems everything is clearer when you read this:
[http://www.thinkwiki.org/wiki/Ibm-acpi](http://www.thinkwiki.org/wiki/Ibm-acpi)

Sorry, the modules is not "acpi_ibm" but "ibm_acpi".

So in /etc/modules:
```

ibm_acpi

```

Once "ibm_acpi" is loaded, it think it is pretty much the end of it.

To turn on the experimental features, add
```

options ibm_acpi experimental=1

```
to the file /etc/modprobe.d/ibm_acpi.modprobe

This could help:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu/Breezy_on_a_ThinkPad_T42](http://www.thinkwiki.org/wiki/Installing_Ubuntu/Breezy_on_a_ThinkPad_T42)

---

### Post by bigblop on 2006-02-21
I still don't see why I should turn on:

options ibm_acpi experimental=1

what does it do?? Do I risk anything getting fried??

---

### Post by antidrugue on 2006-02-21
[QUOTE=bigblop]I still don't see why I should turn on:

options ibm_acpi experimental=1

what does it do?? Do I risk anything getting fried??[/QUOTE]

Turning it on won't do anything by itself. It will only give you the option of changing fan speed, with
```

echo enable >/proc/acpi/ibm/fan
echo disable >/proc/acpi/ibm/fan

```

for example...

---

### Post by bigblop on 2006-02-21
Wrong again. I now have this in:

/etc/modprobe.d/ibm_acpi.modprobe

options ibm_acpi hotkey=enable,0xff9f,experimental=1

I did a reboot and tried:

johs@ubuntu:~$ echo enable >/proc/acpi/ibm/fan
bash: /proc/acpi/ibm/fan: No such file or directory
johs@ubuntu:~$

there is no folder/program called "fan" in the dir /proc/acpi/ibm, as I mentioned earlier.

it exist in:  /proc/acpi

but I will not mess with that because I don't know what it is.

---

### Post by antidrugue on 2006-02-21
What gives you
```

lsmod | grep -i ibm

```

0 or 1?

I don't know about this specific laptop model...

Sorry I couldn't really help you. I'm sure it's nothing complicated though...

---

### Post by bigblop on 2006-02-22
johs@ubuntu:~$ lsmod | grep -i ibm
ibm_acpi               17908  0
johs@ubuntu:~$


besides I don't really need to be able to turn on/off the fan completly so I guess there is no reason to use the experimental=1 option and it should be enough just to have the ibm-acpi module loaded.

---

### Post by alan.mckinnon on 2006-02-22
You wrote:

"and it seems to work fine, I am not sure I would like to experiment[/QUOTE]"

Everything you need comes with the kernel. When maintainers build a kernel, it's normal to switch on the support for pretty much all possible hardware. On your machine, you will find this as a module. Which basically means that it's a file on the disk somewhere and the kernel proper will load the module when it needs it, or when you tell it to load it. At that point the module is available for use and the hardware it refers to can be controlled.

You can load the module manually yourself every time you boot by using the command "sudo modprobe <modulename>" without quotes, and insert the correct module name.

Or, you can get the system to do it for you at every boot by adding the module name to the end of the file /etc/modules. There's not much to experiment with, the module either loads and works or it doesn't :-)

You have to be root to edit that file, so you'll need to sudo first

---

### Post by bigblop on 2006-02-22
What I mean by experirment was that I don't need to turn on:

options ibm_acpi hotkey=enable,0xff9f,experimental=1

in the file:

/etc/modprobe.d/ibm_acpi.modprobe

since I don't have /proc/acpi/ibm/fan

and that is needed to use the experimental=1 option

---

