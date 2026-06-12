---
title: "Where can I find system information?"
date: 2006-03-23
forum: General Help
---

### Post by jms830 on 2006-03-23
I want to know my RAM, my processor speed, and etc.

I know in windows you can just right click on My Computer and go to properties... is there anything in Ubuntu similar? A place to find these things?

Thanks.

---

### Post by hajk on 2006-03-23
Does Linux/Ubuntu have information? Linux/Ubuntu has LOTS of information, probably more information than you'll ever need! 
Have a look at the /proc directory...

---

### Post by noswal on 2006-03-23
Applications> System Tools > Sytem Monitor  and/or install ProcMeter

---

### Post by Ramses de Norre on 2006-03-23
system > administrations > device manager
But it doesn't show many info for me..
Otherwise in terminal: lshw, lspci, lsusb, less /proc/cpuinfo (and other files in proc)
Or sudo apt-get install hardinfo (shows more info than device manager.)

---

