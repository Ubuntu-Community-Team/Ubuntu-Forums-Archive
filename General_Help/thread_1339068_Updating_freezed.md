---
title: "Updating freezed"
date: 2009-11-27
forum: General Help
---

### Post by jis on 2009-11-27
I installed Xubuntu 9.10 to a friend's computer. Installation is slower than with some other distros, but I guess it is worth waiting for good OS. Then I started update by Update manger. It seemed to freeze at some point; the indicator did not change in several minutes. All I could do was Alt-SysRq-SUB to reboot and the reboot failed. "apt-get check" helped in recovery mode. Still there are a lot of "serial8250: too much work for irq18" messages in dmesg. Another special problem with this installation is that the Master track does not have effect in sound, but the PCM track has.

---

### Post by Riffer on 2009-11-28
You have a hardware problem.  Its found at the interrupt address 18 (irq 18 ).  To help you figure out what hardware it is you can use this command in your terminal 

> cat /proc/interrupts

This will give you what hardware is tied to what irq number.  On my system irq 18 is to a usb port.  If its the same to you then I would try removing anything hooked to a usb port, if you have a usb mouse and keyboard then try moving them to other ports etc.

---

