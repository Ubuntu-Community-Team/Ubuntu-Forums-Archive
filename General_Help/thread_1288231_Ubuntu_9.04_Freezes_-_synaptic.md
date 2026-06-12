---
title: "Ubuntu 9.04 Freezes - synaptic"
date: 2009-10-11
forum: General Help
---

### Post by Pvt_Beeano on 2009-10-11
Just made the switch from XP to Ubuntu but I'm having a few issues.  I'll try and be a clear as possible but I am new to Linux so appologies in advance if I'm missing something obvious, I have been searching the forums and trying to fix this myself.

Initially I did a clean install of 9.04 and can boot to the desktop but after a minute or two the GUI locked up.  I did some searching around and found that adding this to grub's boot options helped as the problem may lie with the wrong tasks being sent to the wrong core in a multi-core cpu;

> noapic nolapic pci=noacpi

The problem with this is that I only get one core of my cpu working so I took out all but;

> pci=noacpi

The system now boots and works for a seemingly random period of time, although launching synaptic, add/remove... or apt from the command line results in an instant freeze.

Here is /var/log/dmesg with only pci=noacpi in the boot options;

[http://www.sendspace.com/file/wgx3mu]("http://www.sendspace.com/file/wgx3mu")

And here it is with all three options;

[http://www.sendspace.com/file/tn19rk]("http://www.sendspace.com/file/tn19rk")

Hope sendspace is okay, let me know if I should use something else.

The only other things I've done since installation is to add VLC and install some drivers to OSS working with my X-Fi card.  I'd really like to be able to use both cores of my cpu.
[B]
Thanks in advance for any help[/B].

Hardware specs for info;

Shuttle SD32G5 with 2Gb of RAM, Intel C2D@2.13, Nvidia 7600GT and Creative X-Fi

---

### Post by Pvt_Beeano on 2009-10-11
Bump

---

### Post by Pvt_Beeano on 2009-10-11
Bump

---

### Post by Pvt_Beeano on 2009-10-11
Bump

---

### Post by bailbath on 2009-10-11
Did you use for the nvidia card the restricted/hardware drivers gui in administration menu.
Ian

---

