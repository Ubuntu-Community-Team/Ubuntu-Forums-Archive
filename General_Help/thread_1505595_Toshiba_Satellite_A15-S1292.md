---
title: "Toshiba Satellite A15-S1292"
date: 2010-06-09
forum: General Help
---

### Post by CharlesJWelsh on 2010-06-09
For some reason Ubuntu and my laptop have not been co-existing very well since Karmic. Juanty worked FINE. Karmic constantly froze. Lucid constantly says low graphics mode... I'm talking once an hour... Sometimes more... What do I do?:confused:

---

### Post by 666f6f on 2010-06-09
Hello Charles,

Let's try to fix the graphics first. Can you post the output of ```
sudo lshw -c display
```

---

### Post by CharlesJWelsh on 2010-06-09
```

  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:10 memory:d8000000-dfffffff(prefetchable) memory:d0000000-d007ffff ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:20000000-27ffffff(prefetchable) memory:2c000000-2c07ffff

```

I am attempting to intall the 855GM Drivers and I get this error... 
```

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver: 

Driver Name    : i915
Description    : Intel 830M/845G/852GM/855GM/865G/915G/915GM Driver
Architecture   : I386
Build Date     : 20041217
Kernel Module  : i915

Optional Information

Driver Version      :  
Special Description :  

Press ENTER to continue or CTRL-C to exit.


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Select from the following options:

  1. Install driver (default)
  2. Uninstall driver

Enter reponse [1-2], or CTRL-C to exit












DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.

Compiling new agpgart module...

ERROR: AGPGART module did not compile


ERROR: AGPGART module did not compile - AGP module turned off in kernel ??

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

---

### Post by 666f6f on 2010-06-09
Unfortunately, there seems to be some known issues with i845, i855 and other 8xx chips (you own an i855).

You can experiment with several different settings documented [here]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes"). You may or you may not find a combination which resolves all issues.

Out of curiosity, why did you try to install DRI? As far as I know it's not the a driver for your graphics card.

---

### Post by CharlesJWelsh on 2010-06-09
Because it claimed to be the fix for 855GM chipsets... IDK What i am doing... I'm not recieving any help that... well... actually helps me. So I was trying to figure it out on my own. I hate my toshiba.

---

### Post by 666f6f on 2010-06-09
> **CharlesJWelsh said:**
> Because it claimed to be the fix for 855GM chipsets... IDK What i am doing... I'm not recieving any help that... well... actually helps me. So I was trying to figure it out on my own. I hate my toshiba.

It would be a complicated situation even for people that know what they were doing. I would suggest to downgrade to Jaunty which is know to work, unless there is a specific reason you want to keep 10.04.

---

