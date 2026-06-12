---
title: "4th GB of RAM in a 64-bit OS"
date: 2011-03-31
forum: General Help
---

### Post by muszek on 2011-03-31
I have a Samsung R60plus notebook with 2x2GB RAM sticks.  BIOS sees 4 GB.
I'm running 64-bit Ubuntu 10.10:
```
muszek@homer:~$ uname -a
Linux homer 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
```
but only 3GB of RAM are recognized:
```
muszek@homer:~$ free
             total       used       free     shared    buffers     cached
Mem:       3089892    2202424     887468          0       7288     900808
-/+ buffers/cache:    1294328    1795564
Swap:      2046972          0    2046972
```

What's the reason and how to fix it?

---

### Post by Jouke74 on 2011-03-31
Are you sharing RAM with your "videocard"? 
(Still 1024 Mb would be a lot for that).

---

### Post by muszek on 2011-03-31
how do I check that?  somewhere in bios?

---

### Post by mastablasta on 2011-03-31
easies wy is to search for specification of notebook or check the lscpi and see what card you have. 
 
yes some newer graphics card do use 1GB of ram (shared)
 
edit: 
in BIOS there is usualyl an option to reduce that amount of shared RAM (if this is the case here)

---

### Post by sanderj on 2011-03-31
> **muszek said:**
> I have a Samsung R60plus notebook with 2x2GB RAM sticks.  BIOS sees 4 GB.
I'm running 64-bit Ubuntu 10.10:


What's the reason and how to fix it?

You could my memory-check-script from [http://www.appelboor.com/check-my-hardware.py](http://www.appelboor.com/check-my-hardware.py)

Run it as root to get all details.

```

wget http://www.appelboor.com/check-my-hardware.py
sudo python check-my-hardware.py 


```

---

### Post by muszek on 2011-03-31
```
check-my-hardware.py - version: SJ 2011-03-13
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3069 MB as usable
BIOS offers 3069 MB as 'modified' usable
Memory seen by OS 3017 MB
BIOS version 04/16/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 1027 MB
Memory difference between BIOS offering and memory seen by OS 52 MB
Memory difference between DIMM hardware and memory seen by OS 1079 MB

ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole rempapping / hoisting' in your BIOS to get more usable memory

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: DIMM DRAM Synchronous
          size: 2GiB
          description: DIMM DRAM Synchronous
          size: 2GiB

Finished
```

thanks, I'll follow these advices

---

### Post by muszek on 2011-03-31
I've upgraded BIOS to the latest available on Samsung's website (Oct. 2008, [http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=&prd_mdl_cd=&prd_mdl_name=NP-R60PLUS](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=&prd_mdl_cd=&prd_mdl_name=NP-R60PLUS) ), but still see 3GB.  Neither BIOS version offered anything resembling "memory hole rempapping / hoisting".

Anything else I could do?

---

### Post by plucky on 2011-03-31
> **muszek said:**
> I've upgraded BIOS to the latest available on Samsung's website (Oct. 2008, [http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=&prd_mdl_cd=&prd_mdl_name=NP-R60PLUS](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=&prd_mdl_cd=&prd_mdl_name=NP-R60PLUS) ), but still see 3GB.  Neither BIOS version offered anything resembling "memory hole rempapping / hoisting".

Anything else I could do?

What about running Memtest+ from the Grub Menu?

Does that show all the memory or just the 3Gb?

---

### Post by sanderj on 2011-03-31
> **muszek said:**
> I've upgraded BIOS to the latest available on Samsung's website (Oct. 2008, [http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=&prd_mdl_cd=&prd_mdl_name=NP-R60PLUS](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=&prd_mdl_cd=&prd_mdl_name=NP-R60PLUS) ), but still see 3GB.  Neither BIOS version offered anything resembling "memory hole rempapping / hoisting".

Anything else I could do?

Did you put in the memory yourself? If so, what is the specification of the max memory the device can handle? Because ... maybe it can not handle more than 3 GB ... (the older the hardware, the less max memory it can handle).
Maybe you need the exact type of your hardware to find the exact max memory spec.

FWIW: there are two PDF-manuals on the site you gave ... which are .EXE-files ... which I'm not downloading ...


EDIT:

The different product numbers for this product:

NP-R60FY01/SUK, NP-R60FY0N/SUK, NP-R60FY0L/SUK, NP-R60FY0K/SUK, NP-R60FY0M/SUK, NP-R60FY0E/SUK, NP-R60F002/SUK, NP-R60FY05/SUK, NP-R60/FY0/SUK, NP-R60FY0C/SUK, NP-R60FY0D/SUK, NP-R60FY08/SUK, NP-R60FY07/SUK, NP-R60/A00/SUK 

So which is yours?

For example: for the NP-R60FY0L-SUK the website [http://www.laptopsdirect.co.uk/Samsung_R60_Plus_Laptop_NP-R60FY0L-SUK/version.asp](http://www.laptopsdirect.co.uk/Samsung_R60_Plus_Laptop_NP-R60FY0L-SUK/version.asp) says "RAM - 2 GB (installed) / 2 GB (max)" ...

---

