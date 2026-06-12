---
title: "M/B Monitoring Question"
date: 2006-03-19
forum: General Help
---

### Post by indytim on 2006-03-19
I'm getting ready to build my wife's new PC in the near future.  I'm planning on loading Ubuntu at the startup of the PC.  I'm going to be using an Intel M/B with a P4 Prescott processor.  Being fairly new to Ubuntu, I'm not totally familiar with all of the options on the apps.  I have two questions relative to the new build:

1.  Is there an equivalent to the M/B monitoring app that ships for Windows from Intel?  Looking for a specific app to monitor the critical voltages and temps (especially important with the Prescott processor).

2.  Been a while since I did an install of Ubuntu.  At install is it possible to designate multiple partitions on the h/d?  I'm going to be using an 80G Seagate SATA for the build and would probably want to identify 2 - 40G partitions to startout.

Thanks,

IndyTim

---

### Post by taurus on 2006-03-19
1.  You can use lm_sensors to monitor all the goodies that comes with the mobo and hddtemp to monitor the temp of your harddrive...  :) 

2.  Yes, you can partition your harddrive anyway you want.  When you get to the partition screen, pick manual and divide it into three primaries since you need one for swap.

---

