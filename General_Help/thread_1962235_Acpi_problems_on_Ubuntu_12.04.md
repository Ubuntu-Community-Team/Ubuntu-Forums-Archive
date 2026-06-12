---
title: "Acpi problems on Ubuntu 12.04"
date: 2012-04-20
forum: General Help
---

### Post by venividivici24 on 2012-04-20
I have a Compaq Presario SR1010V desktop computer from 2004. [http://h10025.www1.hp.com/ewfrf/wc/product?product=448452&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=448452&lc=en&cc=us&dlc=en&lang=en&cc=us)

I have installed a NVIDIA 8400GS PCI not PCI-E graphics card, a Pentium 4 processor, and a 320gb hard drive.

I have Windows 8 Consumer preview, Windows XP Home, and Ubuntu installed on the 320gb hard drive, and Windows 7 Enterprise Trial installed on the original 40gb hard drive.

Every time I try to shut down Ubuntu from the menu, it hangs on the Ubuntu screen, I can hear everything turn off, like the hard disks powering down and the fans spinning down, but to completely shut down the computer, I have to press the physical power button.

The physical power button doesn't work correctly either. If I just PRESS it, not hold it down, the computer shuts down immediately WITHOUT going through the shutdown process

Suspend doesn't work either, there is no option in the menu by the "Shut Down" option, and I have it set to suspend after 10min of inactivity that doesn't work either. I have followed instructions from this link on some tests and debugging: [https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)
I did the tests, and returned with the error, "No kernel Support" on the test below.

dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend

and returned "bootlean=false" on this test.

dbus-send --system --print-reply --dest="org.freedesktop.UPower" --type=method_call --reply-timeout=6000 /org/freedesktop/UPower org.freedesktop.DBus.Properties.Get string:org.freedesktop.UPower string:CanSuspend

I noticed these problems on Ubuntu 10.10, the first version I installed; and I happened to have a 9.10 disc that I had burned; same problems, at least in "live" mode. ( Ubuntu 11.04 and 11.10 don't work; they won't even boot off the cds).

Hibernation does work, but I still have to press the physical power button to complete the shutdown.

I hope that there is a way to fix this, because it is extremely anoying. Perhaps use the old acpi-support instead of pm-utils because this is an old computer?

I hope that I have given enough details, and if I put this in the wrong section, I'm sorry; first post.... :)

---

