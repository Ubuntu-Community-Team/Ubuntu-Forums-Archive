---
title: "panel not responding......"
date: 2009-08-27
forum: General Help
---

### Post by muctadir on 2009-08-27
i am having some problem with the panel. when i turn on ubuntu, the panel does not response. if i click on it nothing happens. i cant access any of my applications or use any of the shortcuts. i have to restart my computer to make the panel working...

please help me to fix my panel.

thanks in advance..............

---

### Post by NoaHall on 2009-08-27
Is your graphics card driver installed/enabled? This can sometimes affect things. Have you changed things which start up with your system at all?

---

### Post by muctadir on 2009-08-27
i dont know if the graphics card is enabled or not. please tell me how to find out.....

and i did not changed any settings that can affect the start up. besides when i restart my computer the panel is ok and works fine....

---

### Post by NoaHall on 2009-08-27
Check the driver in use here -
System -> Administation -> Hardware Drivers. 

Enable special effects here -
System -> Preferences -> Apperance -> Visual Effects

---

### Post by muctadir on 2009-08-27
the visual effects are set to normal. there is no driver in use and the driver list is empty...

---

### Post by NoaHall on 2009-08-27
Run lspci in a terminal and post what the output is

---

### Post by muctadir on 2009-08-27
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

