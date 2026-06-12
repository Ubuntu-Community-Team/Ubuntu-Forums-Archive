---
title: "Can't change fan speed? Help."
date: 2011-05-28
forum: General Help
---

### Post by 381hfk328fn38d1 on 2011-05-28
so basically here is what I did

sudo pwmconfig

This is what I get:

Found the following devices:
hwmon0 is acpitz
hwmon1/device is thinkpad

Found the following PWM controls:
hwmon1/device/pwm1
hwmon1/device/pwm1 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) 

So I type y and then this:

hwmon1/device/pwm1_enable stuck to 2
Manual control mode not supported, skipping hwmon1/device/pwm1.
There are no usable PWM outputs.
[B]
Why won't it let me go to manual mode?[/B]

---

### Post by linuxinstalledfromhdd on 2011-05-28
Have you updated the BIOS on this since it was made?

---

### Post by 381hfk328fn38d1 on 2011-05-28
.No, I haven't actually. Btw, just to make sure, if I upgrade to the new BIOS, how do I revert to the old BIOS if Ubuntu won't work with it?

---

### Post by linuxinstalledfromhdd on 2011-05-28
You would need to start a trouble ticket for support from the manufacture of that laptop.  And you might want to double-check to see if they provide their customers with each updated version of bios they have released for your make/model of laptop.  That way you can always reflash your bios back to a previous version.   Also research what you are doing first.  Flashing your BIOS can damage your system if you don't know what you are doing.  That's why I recommend you contact the manufacture and ask them for support.

---

### Post by wildmanne39 on 2011-05-28
> **philipphfbr said:**
> so basically here is what I did

sudo pwmconfig

This is what I get:

Found the following devices:
   hwmon0 is acpitz
   hwmon1/device is thinkpad

Found the following PWM controls:
   hwmon1/device/pwm1
hwmon1/device/pwm1 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) 

So I type y and then this:

hwmon1/device/pwm1_enable stuck to 2
Manual control mode not supported, skipping hwmon1/device/pwm1.
There are no usable PWM outputs.
[B]
Why won't it let me go to manual mode?[/B]
Hi, unless you have a real good reason to I would not force a change in fan speed, let it be controlled auotnmatically.

---

### Post by 381hfk328fn38d1 on 2011-05-28
.BIOS succesfully updated, same error:

hwmon1/device/pwm1_enable stuck to 2
Manual control mode not supported, skipping hwmon1/device/pwm1.
There are no usable PWM outputs.

Well, I don't have a REAL good reason to want to change the fan speed, but I like to use my laptop in my lap sometimes and it does get quite uncomfortable to handle after a while.

---

### Post by Hedgehog1 on 2011-05-28
For many (but not all folks) this improves the function of the laptop fan:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-28
> **philipphfbr said:**
> BIOS succesfully updated, same error:

hwmon1/device/pwm1_enable stuck to 2
Manual control mode not supported, skipping hwmon1/device/pwm1.
There are no usable PWM outputs.

Well, I don't have a REAL good reason to want to change the fan speed, but I like to use my laptop in my lap sometimes and it does get quite uncomfortable to handle after a while.
Hi, to keep the laptop cool you need like a small cutting board or something like that to put it on then put it on your lap, or you cover up the fan holes and it will get hot,also I used a chiling pad for my laptop, you can get one for about $20.00.

---

### Post by lmn. on 2011-05-28
You could try cleaning off the dust if you don't mind voiding your warranty.. It's probably clogged.

---

### Post by el_koraco on 2011-05-28
Do you perchance have an ATI card?

---

