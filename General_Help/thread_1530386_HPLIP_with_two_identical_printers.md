---
title: "HPLIP with two identical printers"
date: 2010-07-13
forum: General Help
---

### Post by Icehawk on 2010-07-13
After upgrading cups to latest version (1.4.3) hplips stopped working, i tried the workaround of using the usb drivers instead of the hplips one, but the issue is that i have two identical (laserjet 1320) printers, and it recognizes both printers as being just one... sometimes it prints to the first one, sometimes to the second one, which is an issue, because i have one printer loaded with 8.5x11 pages, and the other one with 8.5x13 pages

Im open to any suggestion

Im using ubuntu 10.04 LTS

---

### Post by Morbius1 on 2010-07-13
I've never come across this question before and there's no way for me to try to reproduce your situation. I'm curious though, do you have different names for each printer?

And when you run this command what do you see:
```
sudo cat /etc/cups/printers.conf
```So for example it would look something like this
> <DefaultPrinter [COLOR=Blue]HP1320[/COLOR]>
Info HEWLETT-PACKARD LASERJET 1320
Location XXXX
MakeModel HP Laserjet 1320 hpijs, 3.10.2rc1.9
DeviceURI hp:/usb/Laserjet_1320?serial=[COLOR=Sienna]MY16G1C45TIT[/COLOR]Do you have two entries that differ by name ( [COLOR=Blue]HP1320 ) [COLOR=Black]and serial number ( [/COLOR][/COLOR][COLOR=Sienna]MY16G1C45TIT[/COLOR][COLOR=Sienna] [COLOR=Black]) or just one?[/COLOR]
[/COLOR]

---

