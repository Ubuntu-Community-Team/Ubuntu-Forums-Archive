---
title: "Battery not recognised"
date: 2012-09-06
forum: General Help
---

### Post by drshovan on 2012-09-06
I have installed Ubuntu 12.04 LTS as dual boot in my ACER ASPIRE 5745G laptop which has a WIN 7 Home Prem preinstalled in C: , I have installed it from windows 7 by using a Windows installer from the official Ubuntu download site.My ubuntu has been installed in a separate partition of D:  When I am using ubuntu in battery, then though battery indicator is being shown at right top panel, but it's showing Battery not present. So I can't understand how much battery power is still there using on battery, though when the power cord is onto battery is getting silently charged. Anotrher thing is that if by going to command terminal if i run 

dr_shovan@ubuntu:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      4400 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
cycle count:          0
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            BAT1      
serial number:           11        
battery type:            11        
OEM info:                11        



Please help me out..

---

### Post by asmolinski on 2012-09-15
Is it like that all the time? For me it says no battery present on boot-up but after a few minutes it shows it.

---

