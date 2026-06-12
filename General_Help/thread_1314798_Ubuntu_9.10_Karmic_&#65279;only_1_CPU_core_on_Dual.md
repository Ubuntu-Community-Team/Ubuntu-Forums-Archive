---
title: "Ubuntu 9.10 Karmic &#65279;only 1 CPU core on Dual core"
date: 2009-11-04
forum: General Help
---

### Post by regor210 on 2009-11-04
Solved
&#65279;Only 1 CPU core on Dual core system.
Ubuntu 9.10 Karmic Koala was lagging. When I checked System>Administration>System Monitor It showed only 1 CPU. So I tried $ cat /proc/cpuinfo 
same 1 CPU.  So here is how I fixed it.

On my AMD x2 Dual core I to accesses my BIOS setup utility by holding down the Del key when starting my computer.

I used the arrow keys to highlight POWER and scrolled down to ACPI APIC SUPPORT and pressed enter to select Enabled.

Problem solved.

ACPI APIC SUPPORT  was disabled by default.
I never needed to do this with other versions of Ubuntu.
  
Here is a link to another fix that I did not try due to Grub 2.   
 [http://ubuntuforums.org/showthread.php?t=1144905](http://ubuntuforums.org/showthread.php?t=1144905)

---

