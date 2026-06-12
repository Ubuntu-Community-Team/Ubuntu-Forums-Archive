---
title: "ubuntu 10.04 freezes"
date: 2010-06-24
forum: General Help
---

### Post by launchy on 2010-06-24
to me, ubuntu freezes from time to time to the point that i cant use my mouse and keyboard. instead of a force shutdown using the power button, what can i do to close all the programs that i have loaded? 

thanks.

---

### Post by ajgreeny on 2010-06-24
With no keyboard or mouse input, I'm afraid there is no alternative.  Perhaps enable autosave on all apps that offer it, so at least they should offer to restore files not shutdown properly.

Also try holding down Alt Gr+Sys Rq(Right Alt+Print Screen) then slowly, slowly typing R E I S U B, but if the keyboard is dead, it probably will not do anything.

You could also try Ctrl+Alt+F1, and then shutting down from the cli with ```
sudo shutdown -h now
```but once again that will only work if the keyboard is actively accepting key presses.

You really need to figure out what is causing the freezes, so tell us more detail of your hardware, starting with the output from ```
lspci
``` in terminal.

---

### Post by launchy on 2010-06-24
here is my system specs from the terminal

"00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
04:01.0 Communication controller: Conexant Systems, Inc. Device 2f40
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)"

and 1GB RAM

mostly used programs:
firefox with approximately 10 tabs
urban terror
pidgin
movie player
google chrome
compiz and basic effects are enabled
gnome do

---

### Post by gadelat on 2010-12-24
hey, i have this problem too, what is cousing this lagging?

---

