---
title: "Cursor gets stuck between X screens"
date: 2010-08-05
forum: General Help
---

### Post by Turaiel on 2010-08-05
Hey everyone. I have quite an interesting problem here. I have dual monitors that I have set up with two separate X screens with the nVidia control panel. For some reason at times when I move my mouse between the two screens, the cursor will start flickering rapidly between the adjacent edges of the screens and the system will become completely unresponsive, forcing me to do a hard reboot (the keyboard doesn't have a SysRq key).

What could be causing this, and what can I do to fix it?

---

### Post by Turaiel on 2010-08-06
*bump*

The problem occurred on me again last night. It seems to happen when the cursor moves rapidly between screens.

---

### Post by squarooticus on 2010-10-16
In the process of trying to solve a different problem the other day, I managed also to eliminate this one.  By adding "noirqdebug" to my kernel command line, I eliminated:

(1) a freezing problem on my Lucid MythTV box (Celeron 1200, Gigabyte 965P-DQ6).

(2) a problem in which my pcHDTV cards would, after a day or so, stop working, requiring a reboot.

(3) this problem (the mouse cursor getting stuck between X screens) on my Lucid desktop machine (i7-920, MSI MS-7522).

(4) the problem in which VDPAU output on my desktop (which has 4 heads in Xinerama mode rather than TwinView) with nvidia 260.19.06 would arbitrarily not work (by which I mean it would display one frame every few seconds and consume all of CPU), requiring me to restart X, sometimes several times in a row, to resolve.

I never before checked for it, but I suspect the Linux kernel is, in some modes and on some hardware configurations, disabling IRQ lines that are serving multiple devices when an unserviceable interrupt is received.  With noirqdebug, this "feature" is disabled and the interrupt is simply thrown away.

I would be curious to hear if others have success with this.  Try combinations of:

noirqdebug
irqpoll
acpi=off
pci=nomsi
noapic
nolapic

It's sad that I need to go through this.  I complained about this once before, several years ago, when a different piece of hardware also had problems without noirqdebug.  Insufficiently-tolerant/excessively-strict error handling causes more problems than it solves.

---

### Post by Turaiel on 2010-10-16
I'm glad that someone finally found my thread and replied to it. I'll have to give this a try. How would I go about adding that?

---

### Post by squarooticus on 2010-10-17
> **Turaiel said:**
> I'm glad that someone finally found my thread and replied to it. I'll have to give this a try. How would I go about adding that?

The best way to try it once is to go to the grub menu when you boot up, "e"dit the default boot option, and add "noirqdebug" to the end of the "linux /vmlinuz-..." line.  If you want to add it permanently, edit /etc/default/grub, add "noirqdebug" to the GRUB_CMDLINE_LINUX_DEFAULT variable, and run update-grub.

---

### Post by Raven17 on 2011-02-17
I need to try this fix.

It doesn't seem to matter if I used the stock Lucid drivers or the latest beta drivers.  

It is annoying as hell when the cursor wedges and I lose all of my open work.

GRRRRRRRRRRRRRRR!

Thanks for the posting this and for the tweak!:D

---

### Post by joudard on 2011-08-31
I'm pretty interested by this solution but I'm not using grub but ubuntu only station where should I set these parameters 

using ubuntu 10.4

Thanks

---

### Post by twigcustom on 2012-02-19
Ubuntu 10.10, Xorg 1.9.0, nv-control 1.16, Geforce FX5200 NV34 PCI 256Mb dual VGA outs, Geforce 9500GT G96 PCIe 1 Gb DMS59 out, nVidia 173 driver, Separate X screens

I have been having similar issues to varying extents. Sometimes the mouse would stick as stated above, but sometimes the mouse was not involved. Sometimes X would freeze, sometimes crash, sometimes Xorg or /usr/bin/x :0 -nr would be hogging 100% of one CPU. Sometimes i could get to another TTY but it was a crapshoot if restarting the service would work, and then sometimes i couldnt even get to the other TTY. And finally sometimes i could reisub while others required a hard reset.
I tried the above "noirqdebug" with no results as well as physically removing cards and some other workarounds that google came up with.

In my case the problem ended up being PEBKAC: The installation of the 9500 was the first time I had used the PCIe slots on this mobo and i didn't realize that one of the slots was a x4 and the other was x16. So there was an obvious bottleneck that caused the problems.

---

