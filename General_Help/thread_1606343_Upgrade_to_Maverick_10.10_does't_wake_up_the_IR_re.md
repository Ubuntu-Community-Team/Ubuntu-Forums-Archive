---
title: "Upgrade to Maverick 10.10 does't wake up the IR remote"
date: 2010-10-26
forum: General Help
---

### Post by PrvSAT on 2010-10-26
I worked with Lucid 10.04 and 2.6.32-22 kernel. With 2.6.32-24 kernel I was not able to wake the system with a remote despite the settings in rc.local so I was told that 2.6.32-22 will fix the problem and it did. 
I had the system working almost flawless with XBMC media player. 

After the upgrade to Maverick 10.10 with default kernel 2.6.35-22-generic  #35 the remote does not wake up the system anymore from standby.

My curent etc/rc.local is:
```
sudo sh -c 'echo "USB6" > /proc/acpi/wakeup'
sudo sh -c 'echo "USB5" > /proc/acpi/wakeup'
sudo sh -c 'echo "USB4" > /proc/acpi/wakeup'
sudo sh -c 'echo "USB3" > /proc/acpi/wakeup'
sudo sh -c 'echo "USB2" > /proc/acpi/wakeup'
sudo sh -c 'echo "USB1" > /proc/acpi/wakeup'
sudo sh -c 'echo "USB0" > /proc/acpi/wakeup'

exit 0

```For example, even if the USB6 is enabled in rc.local, after bootup when lsusb I get:
```
P0P2      S4    *disabled  
P0P3      S4    *disabled  
P0P1      S4    *disabled  pci:0000:00:1e.0
UAR1      S4    *disabled  pnp:00:0c
EUSB      S4    *disabled  pci:0000:00:1d.7
USBE      S4    *disabled  pci:0000:00:1a.7
P0P5      S4    *disabled  
P0P6      S4    *disabled  
P0P7      S4    *disabled  
P0P8      S4    *disabled  pci:0000:00:1c.4
P0P9      S4    *disabled  pci:0000:00:1c.5
GBEC      S4    *disabled  
USB0      S4    *enabled   pci:0000:00:1d.0
USB1      S4    *enabled   pci:0000:00:1d.1
USB2      S4    *enabled   pci:0000:00:1d.2
USB3      S4    *disabled  
USB4      S4    *enabled   pci:0000:00:1a.0
USB5      S4    *enabled   pci:0000:00:1a.1
USB6      S4    *disabled  pci:0000:00:1a.2
P0P4      S4    *disabled  pci:0000:00:1c.0
```I don't understand. What should I do, should I revert to the older 2.6.32-22 kernel?
What could it be done please to be able to wake the system form stand-by with the remote under current Maverick version?

---

### Post by PrvSAT on 2010-10-29
So nobody has this wake-up problem installing the new Maverick?
I am sure that by downgrading the kernel will fix the problem but then why there is so much fuss and music around the new release when things do not work OK?

---

### Post by maverick555 on 2010-10-29
Yes they released with bugs.Try installing the newer kernel. 2.6.36 is out.check it out.

---

### Post by PrvSAT on 2011-02-26
I went back to 10.04 and now I'm back to 10.10 but still the IR wakeup is not fixed with the latest updates.

Hey "maverick555", what 2.6.36 kernel you are talking about? Even now after few months the latest proposed build is 2.6.35-27 but not 36. Are u sure?

Nobody else have this wake up problem from IR remote?

---

