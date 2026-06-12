---
title: "not direct rendering capable    ????????  :("
date: 2009-12-05
forum: General Help
---

### Post by baskar007 on 2009-12-05
I have Ubuntu9.10 installed on my PC. after that i completely removed gnome from Ubuntu and now using KDE4.3*, 

after a long time i have successfully enabled desktop effects.
but still i can't get DirectRendering.

here is the details:

Output of "xdriinfo" 
```

desktop:~$ xdriinfo
Screen 0: not direct rendering capable.

```


"glxinfo"
```

desktop:~$ glxinfo | grep direct
direct rendering: Yes

```


"ls pci"
```

desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

anything todo with apt ? or need more details ?

please help me.

---

### Post by tmcmack on 2010-01-17
Did you ever figure anything out? I have the same situation: xdriinfo says it's not direct rendering capable, but glxinfo says direct rendering: yes. To my newbie eyes, that seems contradictory, and thus I don't know how to diagnose my display problems (i.e. speedy, responsive behavior with most things, but jerky video and hopelessly low framerate on games).

---

### Post by baskar007 on 2010-01-18
> **tmcmack said:**
> Did you ever figure anything out? I have the same situation: xdriinfo says it's not direct rendering capable, but glxinfo says direct rendering: yes. To my newbie eyes, that seems contradictory, and thus I don't know how to diagnose my display problems (i.e. speedy, responsive behavior with most things, but jerky video and hopelessly low framerate on games).
yeah, enabling acpi in kernel was solved this problem for me.
try it.

---

### Post by tmcmack on 2010-01-23
> **baskar007 said:**
> yeah, enabling acpi in kernel was solved this problem for me.
try it.

I tried adding acpi=on and acpi=force in grub2, but no change (after sudo update-grub and reboot). Regardless, I get these results in the terminal:

```

tmcmack$ glxinfo | grep direct
direct rendering: Yes

tmcmack$ sudo dmidecode | grep ACPI
		ACPI is supported

tmcmack$ xdriinfo
Screen 0: not direct rendering capable.
```

Thanks, though -- there must be something else wrong.

---

### Post by dcstar on 2010-01-24
> **tmcmack said:**
> I tried adding acpi=on and acpi=force in grub2, but no change (after sudo update-grub and reboot). Regardless, I get these results in the terminal:

```

tmcmack$ glxinfo | grep direct
direct rendering: Yes

tmcmack$ sudo dmidecode | grep ACPI
		ACPI is supported

tmcmack$ xdriinfo
Screen 0: not direct rendering capable.
```

Thanks, though -- there must be something else wrong.

AFAIK there are no 3D drivers for Intel video chips.

---

### Post by tmcmack on 2010-01-24
> **dcstar said:**
> AFAIK there are no 3D drivers for Intel video chips.

This is a trident video chip. There's troubleshooting info all over the web and this forum about problems with trident cyberblade on Linux. In particular, [this thread]("http://ubuntuforums.org/showthread.php?t=215708") discusses a lot of different (conflicting) information about its capabilities, and the only thing that hasn't been tried to get it really working properly is a custom kernel compile.

---

### Post by schubber on 2010-02-28
Hello,

i just found your Thread, did you solve the problem in the meantime? I have exactly the same problem with a intel 945 graphic set on a fujitsu st5112 laptop. 
After a install of ubuntu 9.10 the buildin screen won't work at all with the intel driver only with the vesa driver. So i downgraded the intel driver to 2.4 (see this howto [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)). Now i have a working screen but poor performance and the same problems as described in your thread.
For additional information see my thread [http://ubuntuforums.org/showthread.php?t=1417280](http://ubuntuforums.org/showthread.php?t=1417280).

---

### Post by baskar007 on 2010-02-28
> **schubber said:**
> Hello,

i just found your Thread, did you solve the problem in the meantime? I have exactly the same problem with a intel 945 graphic set on a fujitsu st5112 laptop. 
After a install of ubuntu 9.10 the buildin screen won't work at all with the intel driver only with the vesa driver. So i downgraded the intel driver to 2.4 (see this howto [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)). Now i have a working screen but poor performance and the same problems as described in your thread.
For additional information see my thread [http://ubuntuforums.org/showthread.php?t=1417280](http://ubuntuforums.org/showthread.php?t=1417280).

use OpenGL instead of using  XRender for compositing. is your kernel have "acpi" enabled.
if not, first add 'acpi=force' to grub file. and then try again.
Best of luck.

---

