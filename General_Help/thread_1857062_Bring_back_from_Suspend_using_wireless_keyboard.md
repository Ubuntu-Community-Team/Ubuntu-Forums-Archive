---
title: "Bring back from Suspend using wireless keyboard"
date: 2011-10-09
forum: General Help
---

### Post by sergiollag1 on 2011-10-09
Is there a way to awake the computer from suspended mode with the keyboard? I have a Logitech wireless keyboard and mouse and they can't bring the pc from suspended mode, i have to use the power button. This is with Ubuntu 11.04.

---

### Post by dave01945 on 2011-10-09
this might be of use have a look then let us know

[http://ubuntuforums.org/showthread.php?p=4466270](http://ubuntuforums.org/showthread.php?p=4466270)

---

### Post by sergiollag1 on 2011-10-12
no luck,
after doing (echo "USB0" > /proc/acpi/wakeup) nothing changes. bellow is what I get before and after i enter the echo command. (maybe because there is an * in front of disabled?)

root@Media-Room:~# cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
P0P4      S4    *disabled  
BR1E      S4    *disabled  pci:0000:00:1e.0
EUSB      S4    *disabled  pci:0000:00:1d.0
USB0      S4    *disabled  
USB1      S4    *disabled  
USB2      S4    *disabled  
USB3      S4    *disabled  
USBE      S4    *disabled  pci:0000:00:1a.0
USB4      S4    *disabled  
USB5      S4    *disabled  
USB6      S4    *disabled  
BR21      S4    *disabled  
BR22      S4    *disabled  pci:0000:00:1c.2
BR23      S4    *disabled  
P0P1      S4    *disabled  
P0P3      S4    *disabled  
P0P5      S4    *disabled  
P0P6      S4    *disabled  
USB8      S4    *disabled  
BR20      S4    *disabled  pci:0000:00:1c.0
BR24      S4    *disabled  pci:0000:00:1c.4
BR25      S4    *disabled  pci:0000:00:1c.5
BR26      S4    *disabled  
BR27      S4    *disabled

---

### Post by Toz on 2011-10-12
You need to have root privileges to do that (even though you don't get an error if you try it as a regular user). Try this command:
```
echo USB0 | sudo tee /proc/acpi/wakeup
```
This will toggle the USB0 entry to make it *enabled.

Issue the same command again to disable the entry.

---

### Post by sergiollag1 on 2011-10-13
ok, i tried what u said:

echo USB0 | sudo tee /proc/acpi/wakeup

and it promted me for my password, so i entered it, but still everything is disabled when i check with:

cat /proc/acpi/wakeup

---

### Post by Toz on 2011-10-13
Can you post back the results of 'cat /proc/acpi/wakeup', again run:
```
echo USB0 | sudo tee /proc/acpi/wakeup
```
and once again post back results of 'cat /proc/acpi/wakeup'?

---

### Post by sergiollag1 on 2011-10-13
it is the same beafore and after i do:
echo USB0 | sudo tee /proc/acpi/wakeup

Device    S-state      Status   Sysfs node
P0P4      S4    *disabled  
BR1E      S4    *disabled  pci:0000:00:1e.0
EUSB      S4    *disabled  pci:0000:00:1d.0
USB0      S4    *disabled  
USB1      S4    *disabled  
USB2      S4    *disabled  
USB3      S4    *disabled  
USBE      S4    *disabled  pci:0000:00:1a.0
USB4      S4    *disabled  
USB5      S4    *disabled  
USB6      S4    *disabled  
BR21      S4    *disabled  
BR22      S4    *disabled  pci:0000:00:1c.2
BR23      S4    *disabled  
P0P1      S4    *disabled  
P0P3      S4    *disabled  
P0P5      S4    *disabled  
P0P6      S4    *disabled  
USB8      S4    *disabled  
BR20      S4    *disabled  pci:0000:00:1c.0
BR24      S4    *disabled  pci:0000:00:1c.4
BR25      S4    *disabled  pci:0000:00:1c.5
BR26      S4    *disabled  
BR27      S4    *disabled

---

### Post by Toz on 2011-10-13
It doesn't look like USB0 is assigned to any device. What does **lsusb** return?

---

### Post by sergiollag1 on 2011-10-14
thanx very much, i got it now, it was EUSB. I tried them all to find out.
i thought the device would get enabled even if nothin was connected to it.

---

