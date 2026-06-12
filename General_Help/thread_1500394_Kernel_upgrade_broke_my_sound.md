---
title: "Kernel upgrade broke my sound?"
date: 2010-06-03
forum: General Help
---

### Post by DustyMP on 2010-06-03
[FONT="Times New Roman"][SIZE="4"]I need a little guidance ladies and gentlemen. Ubuntu 10.04 on a Dell 600m platform. The upgrade to kernel 2.6.32-22 doesn't seem to support my sound card. If I boot with 2.6.32-21 sounds works fine, and I can find it in the hardware tab of the sound preferences. Boot with 2.6.32 and nothing's available there. Now I'm pretty sure the driver must still be intact since it's running under the *-21 revision. I'm not afraid to go trying to go customizing the kernel if need be. But I do have a few questions here:
[LIST=1]
[*]Is my troubleshooting solid or did I miss something?
[*]Obviously the driver is still in the /dev(?) partition, how do I verify it's loading as it should when I boot the *-22 kernel?
[*]I recognize the fact that I could just not take anymore kernel upgrades and run revision *-21 forever, but I also know that in the past when I've unchecked upgrades suggested by update manager that they just show up the next time. Is there a way to prevent updates from being suggested after declining to apply them?
[/LIST]I'm going to bed now, so thank you in advance for your assistance but understand It's going to be a few hours before I'll be back to read responses and expand further if required.[/SIZE][/FONT]

---

### Post by -humanaut- on 2010-06-03
Type lspci

into a terminal and post the results back here. I'd highly advise against trying to customize the kernel.

---

### Post by ajgreeny on 2010-06-03
You can pin a particular version of any application/package to what you already have.
To pin a package version add these lines to  /etc/apt/preferences:

```
Package: name                
Pin: version (number from repos)    
Pin-Priority: 1001
```

---

### Post by DustyMP on 2010-06-03
Thanks AJ, I'll play around with that!

So here's the output from lspci:```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
``` The results were exactly the same for both revisions of the kernel.

---

### Post by bobpress on 2010-06-03
[FONT=Times New Roman][SIZE=4]Same problem for me on HP dv6-1240.  Kernel 2.6.32-21 sounds works fine.  There is a sound card support problem in the new kernel since no sound card shows under the new kernel.

Additional info:
lspci results for both 2.6.32-21 and 2.6.32-22
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
I have reverted back to -21 until there is a solution.
[/SIZE][/FONT]

---

### Post by knifegame on 2010-06-04
same issue.

lspci result from both 2.6.32-21 and 22[SIZE=4][FONT=Times New Roman]:[/FONT][/SIZE]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

I've had consistent problems with audio dropping out prior to this update, but at this point no audio hardware shows up in Sound Preferences post update.

---

