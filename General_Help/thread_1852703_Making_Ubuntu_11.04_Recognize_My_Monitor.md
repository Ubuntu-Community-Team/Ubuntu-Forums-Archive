---
title: "Making Ubuntu 11.04 Recognize My Monitor"
date: 2011-09-30
forum: General Help
---

### Post by ccross13126 on 2011-09-30
I have a new install of Ubuntu 11.04 and it will not recognize my monitor.  It is a Dell S199WFP 19in LCD.  I need to have it recognized so I can set the correct screen resolution of 1440x900.  I'm currently limited to 1280x1024.

Can anyone help me out?

---

### Post by WasMeHere on 2011-09-30
What video card or chip do you use? If you have nvidia (GeForce, nForce, Quadro), you can select a proprietary hardware driver, that can manage your screen much better, and you should be able to get the native resolution.

Enter the terminal command
```
sudo lshw -businfo | grep display
```
to find information about your video card/chip!

---

### Post by ccross13126 on 2011-09-30
> **Olle Wiklund said:**
> What video card or chip do you use? If you have nvidia (GeForce, nForce, Quadro), you can select a proprietary hardware driver, that can manage your screen much better, and you should be able to get the native resolution.

Enter the terminal command
```
sudo lshw -businfo | grep display
```to find information about your video card/chip!

PCI (sysfs)  
pci@0000:00:02.0              display        82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

Thats what I got :)

---

### Post by WasMeHere on 2011-09-30
Look at this thread describing what other people try with the same chip. [_http://ubuntuforums.org/showthread.php?t=1846023_]("http://ubuntuforums.org/showthread.php?t=1846023")

You can also search for *linux 82845G/GL[Brookdale-G]/GE* with an internet browser. With good luck or hard work a solution will appear out of the cyberspace.

Good luck
Olle

---

