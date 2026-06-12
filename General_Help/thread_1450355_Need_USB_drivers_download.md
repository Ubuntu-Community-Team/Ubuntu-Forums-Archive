---
title: "Need USB drivers download"
date: 2010-04-08
forum: General Help
---

### Post by Paul2795 on 2010-04-08
Where can I download drivers for PCI USB 2.0 card with Via chipset? Can anyone out there point me in the right direction.

---

### Post by MooPi on 2010-04-08
Are these items not being recognized ? Run a couple of commands in terminal and post back here. 
```
sudo lshw -html>hardware
``````
lspci>PCI
```

This should dump two files called hardware and PCI in you home folder. You can attach them so we can read.

---

### Post by Paul2795 on 2010-04-09
I did as you suggested. The file 'hardware' was blank, but PCI did contain information some of which I am entering manually below.
 
01:02.0 USB Controller: VIA Technolgies, Inc VT82xxxx USB Controller (rev62)
01:02.1 USB Controller: VIA Technolgies, Inc VT82xxxx USB Controller (rev62)
01:02.2 USB Controller: VIA Technolgies, Inc USB 2.0 (rev65) 
 
I am entering this a public computer as I have not got my own Internet connection for which I will need USB up yet, hence the delay in replying. So where do I go from here?

---

