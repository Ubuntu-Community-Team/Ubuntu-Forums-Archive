---
title: "Occassional BIOS boot freeze anyone else heard of this?"
date: 2009-10-23
forum: General Help
---

### Post by OrangeVixen on 2009-10-23
I recently got a new computer from zareason.com with Ubunto 9.04 preinstalled on it.

I noticed one problem that happens when I shutdown from "Switch users or shut down" menu is that when I go to Shutdown from there, Linux shuts down normally and turns off the MOBO normally and everything goes off.

Regardless of waiting for a few minutes or a day, whenever I turn the computer on again, it gets stuck/freezes at the BIOS boot screen, right after it detects 3 USB massive storage devices and tries to detect #4. It just stays there and the orange HDD activity light on the from panel stays on. I've waited up to an hour and nothing happens.

Pressing the reset button on the front panel does not help, the same thing happens again, it never even gets to the bootup menu or GRUB. Pressing DEL does not work either. I have to turn off the computer and then turn it on again, then the BIOS goes through and reaches GRUB.

I remember reading something like this a few months ago, but I can't remember where.

I have an MSI X58M motherboard, and uname -a outputs:

```

Linux zareason-limbo 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

```

Is there anything else I can try? this does not happen every time and I really don't know what else to do, I already contacted zareason.com and msi.com with no solution.

---

### Post by undecim on 2009-10-23
It could possibly be one of the mass storage devices? Many times I've had USB devices prevent a computer from booting. Try removing a USB device, and if your computer still hangs after pressing  the reset button, plug it back in and try another until the computer boots

If that doesn't work, try removing all USB devices and trying it one more time.

---

### Post by amauk on 2009-10-23
I've had issues with mixed PATA / SATA systems
(SATA hard disks, PATA DVD drive)
PATA device were preventing the machine from POSTing
disconnecting dvd drive solved issue

If this is the case for you, you might want to fiddle around in the BIOS
there's a few options you can change to do with how PATA & SATA interact with each other

---

### Post by dcstar on 2009-10-23
> **OrangeVixen said:**
> I recently got a new computer from zareason.com with Ubunto 9.04 preinstalled on it.

I noticed one problem that happens when I shutdown from "Switch users or shut down" menu is that when I go to Shutdown from there, Linux shuts down normally and turns off the MOBO normally and everything goes off.

Regardless of waiting for a few minutes or a day, whenever I turn the computer on again, it gets stuck/freezes at the BIOS boot screen, right after it detects 3 USB massive storage devices and tries to detect #4. It just stays there and the orange HDD activity light on the from panel stays on. I've waited up to an hour and nothing happens.

Pressing the reset button on the front panel does not help, the same thing happens again, it never even gets to the bootup menu or GRUB. Pressing DEL does not work either. I have to turn off the computer and then turn it on again, then the BIOS goes through and reaches GRUB.
.........

Chances are your MB is trying to boot off one of the USB devices. Go into the BIOS when the problem occurs and check the boot order and specifically if is detecting one of the connected USB devices as a boot device ahead of your hard drive.

---

### Post by P4man on 2009-10-23
Why not ask zareaon? You bought from them for "a reazon" :) I suspect they would know about something like that.

---

### Post by OrangeVixen on 2009-10-23
Already tried asking zareason, I haven't heard back.

If I press TAB quickly enough at the BIOS boot screen, I get to see the text output and it says:

Auto-detecting USB mass storage devices:
1 Detected hispeed
2 Detected hispeed
3 Detected hispeed
4 

If it hangs/freezes, it does so on 4 each time. The problem is that this is intermittent, sometimes it gets stuck there and sometimes it does not.

What BIOS settings should I "fiddle" with?

---

### Post by 3rdalbum on 2009-10-23
I built a computer for a friend which had random freezes during the BIOS POST screen. I moved the RAM to a different slot and that fixed the problem. (I assume a BIOS update would have done the same thing, but the machine was Linux-only).

---

### Post by OrangeVixen on 2009-10-26
With help from another thread, I solved this problem too.

It turns out that I had enabled way too many devices in my BIOS's boot list, so I removed a whole bunch of USB storage devices from the boot list and only had my IDE CD/DVD and my primary SATA HDD listed, this seems to have fixed the boot hang/freeze problem whenever I restarted or shut down from Linux.

I think for some reason Linux registers some USB storage device to the BIOS or something and so on the next boot (warm or cold) it freezes.

---

### Post by Jqzwvt on 2009-11-08
After installing Ubuntu 9.10, I experienced a similar problem on my HP dv9700 series laptop. I did not have this problem on Windows Vista, Windows XP, Ubuntu 8.04, Ubuntu 8.10, Ubuntu 9.04, or Ubuntu 9.10 beta installed on the same machine. I'm not 100% certain that I didn't have problems with Ubuntu 9.10 beta. I also believe the problems appeared after installing bashdb on Ubuntu 9.10 beta and Ubuntu 9.10. I'm not sure how to debug problems before the operating system starts up.

I have several devices enabled, and I will try removing them from my BIOS.

I would be interested to know more about this problem.

---

### Post by OrangeVixen on 2009-11-08
I'nm not a Windows user, this is really my first modern computer. :/

I'm still using Ubuntu 9.04 Jaunty, these are all the things I have tried:

In the BIOS setting (ONLY DO THIS IF YOU ARE SURE YOUR KEYBOARD IS USB 2.0 or you have a PS2 KEYBOARD) disable USB legacy support, this is because some USB devices are not being detected properly.

In the BIOS setting, remove any devices in the boot list that you know you do not have, in fact, only have the CD/DVD Drive and the HDD with Linux on it in the boot list.

See if the same problem occures if you have Linux shutdown -r (restart).

Make sure your USB mouse and keyboard are plugged in snuggly, once I didn't plug it in securely and I got wierd auto detection messages at both the BIOS level and Linux hot plugging.

---

