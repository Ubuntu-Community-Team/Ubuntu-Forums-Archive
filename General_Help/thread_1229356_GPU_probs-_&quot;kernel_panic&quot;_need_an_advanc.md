---
title: "GPU probs- &quot;kernel panic&quot; need an advanced user for this( I think)"
date: 2009-08-02
forum: General Help
---

### Post by kixome on 2009-08-02
Here is the rundown:

I have tried repeatedly (with many different Linux Distro's) to use my PCI ati radeon 9250 gpu. The problem my friends is that I have an HP pavilion a630n with intel integrated graphics. 

when I boot, in any distro it causes a kernel panic (although i have selected pci instead of onboard in the bios thus turning off the onboard graphics {supposedly}) 

Even in windows both gpu's are detected but the intel can be disabled in HW manager. I have tried removing the intel drivers to no avail. 

This is not a problem on my dell where the bios has an explicit option to turn off the onboard graphics. This is also not a problem when using PCIe. 

I am assuming that since the intel graphics use the pci bus, it causes the problem of seeing two graphics adapters.

Any help would be appreciated.

---

### Post by kixome on 2009-08-02
anybody-anybody?

---

### Post by MaxIBoy on 2009-08-02
When, exactly, does the kernel panic occur? During the boot process?

---

### Post by kixome on 2009-08-06
yes during boot, Linux never fully loads. Stopped by kernel panic

---

### Post by kixome on 2009-08-06
anybody, any help appreciated

---

### Post by kixome on 2009-08-12
no help? well thats balls

---

### Post by philcamlin on 2009-08-12
are you able to bootup into the live cd fine?

---

### Post by kixome on 2009-08-20
No I cannot, get kernel panic, which is what happens if I have any distro installed and then install the card and boot(this happens even when i have uninstalled the intel drivers. In xp i can go to hw manager and disable the intel graphics then install the ati card and it JUst works

---

### Post by kixome on 2009-08-20
I will try installing the card tommorrow so i can dmesg and find out exactly what it says

---

