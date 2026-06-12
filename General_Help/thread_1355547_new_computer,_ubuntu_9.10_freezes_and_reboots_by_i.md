---
title: "new computer, ubuntu 9.10 freezes and reboots by itself"
date: 2009-12-15
forum: General Help
---

### Post by tryf_u on 2009-12-15
hey all,

i just got a new computer last week.

-Processors-AMD Phenom(tm) II X3 720 Processor

-Memory- 2*2 GB

-Graphics Card- ATI Radeon 4770 HD

-Motherboard- Gigabyte  GA-MA770-UD3

i installed ubuntu 9.10 desktop amd64 bit on it

since then ubuntu keeps freezing periodically or re-booting by itself.

how can i fix this problam.
how can i find out what causes this problam?

thanks,
Uri

---

### Post by SlugSlug on 2009-12-15
normally a sign of CPU overheating 
install lm-sensors  and check it out

---

### Post by tryf_u on 2009-12-15
lm-sensors doesn't support AMD K10

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

i don't think this is the problem.
i bought a new cpu fan, i have a case fan, a psu fan ..... 

is there a log file i can look in to find out what caused the crash ?

---

### Post by TitanusEramius on 2009-12-15
I've probably still check the temperature is it was me, most (if not all?) bios's support this from inside the bios. Only problem is the computer is idle, so you have to wait a few minutes before reading the temp.

About the log i don't know, but let's hope someone does, because i like to know :)

Te

---

### Post by tryf_u on 2009-12-15
i checked temperature after some time with some programes running:

:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +27.6°C 


as far as i know.... this is a low temp.


so..... what now?

where can i find a log for the linux reboot or freez ?
what should i look for in that log? (init, error, reboot ...)

thanks,
Uri

---

### Post by nx2ho on 2009-12-15
run memtest86+  ( on install CD/DVD )

---

