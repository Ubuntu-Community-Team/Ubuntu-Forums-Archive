---
title: "MSI users help"
date: 2010-01-21
forum: General Help
---

### Post by inuit-joe on 2010-01-21
Ok, i run an MSI U100 netbook, as soon as i upgraded to 9.10 i started having bad problems.
USBs wouldnt recognise the built-in webcam made it go bezerk.
the brightness fliked up and down uncontrollably. now seeing as i use a wireless broadband dongle to connect to the internet i couldnt really update. so i dont know if it has been fixed yet or not.

---

### Post by Zorael on 2010-01-22
The brightness bug can be fixed either by upgrading your bios (1.0G?), by killing off the **gnome-power-manager** process or by running KDE SC and making a custom HAL rule to enable the property **laptop_brightness_in_hardware**.

The webcam/USB bug can be fixed by enabling the **karmic-proposed** repository and upgrading to the **2.6.31-18** kernel, or by blacklisting the **uvcvideo** module - but then you're disabling the webcam.

From [this post](http://ubuntuforums.org/showthread.php?p=8695557);
> **1**: On some hardware, brightness is directly controlled by hardware. Meaning, even without a power manager you could change brightness with Fn keys.

**2**: On further other hardware, when brightness changes a keypress event is fired (either by hardware or kernel), even if keys weren't used to change the brightness - such as if dragging a slider in a graphical environment.

**3**: Most power managers try to "help" hardware change brightness by sending the needed system calls upon catching keypress events that tell it to.

When all (**1**+**2**+**3**) these collide, you get oscillating brightness upon brightness changes. The hardware changes brightness and emits a keypress, which the power manager catches and changes brightness, which the hardware notices and emits a keypress, which the power manager catches and changes brightness - and you get a race.

**4**: Some video drivers set brightness to 0 when setting the screen to dpms sleep, suspend or power off.

In the combined case of **2**+**4**, whenever the screen is told to go to sleep, the driver first sets the brightness to 0 and then powers it off. The hardware notices the brightness change and emits a keypress event. X.Org notices the keypress and wakes the screen. See [bug 415023](https://bugs.launchpad.net/bugs/415023).

This happens with the current Intel driver, for instance. See [bug 453812](https://bugs.launchpad.net/bugs/453812). I patch it to remove the brightness change.

MSI Wind U100 and derivative machines seem struck by all these 4 points. In GNOME you can disable power management completely by killing gnome-power-manager, but it's not as possible to kill off the KDE Powerdevil. However, it's been patched to allow us to make it back off handling brightness by making a HAL rule.

The only other option to easily work around all these (brightness) issues is to upgrade your bios.

---

