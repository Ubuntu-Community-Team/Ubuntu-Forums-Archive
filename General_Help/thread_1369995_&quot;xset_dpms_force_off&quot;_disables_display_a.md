---
title: "&quot;xset dpms force off&quot; disables display and some seconds later it gets enabled"
date: 2010-01-01
forum: General Help
---

### Post by mondalaci on 2010-01-01
The title pretty much describes the issue.  The timespan is sometimes some minutes instead of some seconds.  I've tried unplugging every peripherials and disabling the touchpad, killing every non-critical processes, disabling and enabling Compiz, but nothing has helped so far.

I'm running Karmic on an Acer Aspire 8935G-874G100BN laptop with a Radeon graphics chipset.

I really hope somebody has some wise words to say.  Is there anyone who can reproduce this or is it just me?

---

### Post by caprilo on 2010-01-06
I have exactly the same problem on a Dell Inspiron 1525 with Karmic. This code used to work OK with Hardy. Any ideas?

---

### Post by caprilo on 2010-01-06
Update, if you first kill gnome-power-manager

```
killall gnome-power-manager
```

then the xset code works properly. Of course, by killing this program you lose the automatic energy settings, but that indicates where the conflict is.

---

### Post by De4dSpace on 2010-01-20
Same here, I'll "killall gnome-power-manager" and see if the monitor is still off in the morning.

---

### Post by Zorael on 2010-01-20
**1**: On some hardware, brightness is directly controlled by hardware. Meaning, even without a power manager you could change brightness with Fn keys.

**2**: On further other hardware, when brightness changes a keypress event is fired (either by hardware or kernel), even if keys weren't used to change the brightness - such as if dragging a slider in a graphical environment.

**3**: Most power managers try to "help" hardware change brightness by sending the needed system calls upon catching keypress events that tell it to.

When all (**1**+**2**+**3**) these collide, you get oscillating brightness upon brightness changes. The hardware changes brightness and emits a keypress, which the power manager catches and changes brightness, which the hardware notices and emits a keypress, which the power manager catches and changes brightness - and you get a race.

**4**: Some video drivers set brightness to 0 when setting the screen to dpms sleep, suspend or power off.

In the combined case of **2**+**4**, whenever the screen is told to go to sleep, the driver first sets the brightness to 0 and then powers it off. The hardware notices the brightness change and emits a keypress event. X.Org notices the keypress and wakes the screen. See [bug 415023](https://bugs.launchpad.net/bugs/415023).

This happens with the current Intel driver, for instance. See [bug 453812](https://bugs.launchpad.net/bugs/453812). I patch it to remove the brightness change.

MSI Wind U100 and derivative machines seem struck by all these 4 points. In GNOME you can disable power management completely by killing gnome-power-manager, but it's not as possible to kill off the KDE Powerdevil. However, it's been patched to allow us to make it back off handling brightness by making a HAL rule.

The only other option to easily work around all these (brightness) issues is to upgrade your bios.

---

### Post by mondalaci on 2010-04-06
Yup, that did the trick.  Thanks guys!

> **De4dSpace said:**
> Same here, I'll "killall gnome-power-manager" and see if the monitor is still off in the morning.

---

### Post by Programmer210 on 2010-06-04
This same issue is hitting me with my new Jaunty X86-64 install. This is on a desktop system. The problem does not exist with Hardy on the exact same hardware. It sounds like the issues that Zorael mentions are issues with laptops, so shouldn't be affecting me. I can try killing off the power management daemon, but I would rather not. Any further thoughts?

I've checked the various man pages, and can't find any way to tell any of those components to turn off the display - only "xset dpms force off".

-cg

---

