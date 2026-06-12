---
title: "Visual effects won't work"
date: 2010-07-19
forum: General Help
---

### Post by athenaharmony on 2010-07-19
Hi,
Today I noticed that I cannot enable visual effects on my computer.  When I try to enable them, the screen flickers, enables the effects for just a moment, then flickers back to the previous screen with a dialogue box that says "visual effects could not be enabled".  This is very strange because I was able to enable them when I first installed Ubuntu (in fact, I ran the "extra" visual effects for a while until I decided that it slowed my computer down too much).  I don't know if it is possible that this has something to do with the most recent updates?
I'm not sure exactly what graphics card I have, but it is an ATI Radeon of some sort.
Any help is appreciated!

---

### Post by cariboo on 2010-07-19
It would help if we knew what graphics adapter you have, make/model. Open a terminal and type type:

```
sudo lshw -C display
```

and paste the results in your next post.

---

### Post by athenaharmony on 2010-07-19
This is the output that I get from that code:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=64
       resources: memory:d0000000-dfffffff(prefetchable) memory:f0100000-f010ffff ioport:9400(size=256) memory:f0000000-f00fffff

---

### Post by 3Miro on 2010-07-19
Go to System -> Administration -> Hardware Drivers and see if the proprietary ATI driver has been enabled. You will need that for the effects to work properly.

If the driver is enabled, then try to reinstall it. That is, disable the driver. Reboot (just to make sure). And then install it again.

It is possible that an update to the kernel did not properly register the proprietary driver.

---

### Post by JonnyOSullivan on 2010-07-19
Same Problem here. You're not alone.

---

### Post by athenaharmony on 2010-07-19
Okay, that might be the problem.  It says that I have no proprietary drivers installed on the system.  I am going to go check the ATI site to see about downloading the right one(s).

---

### Post by clhsharky on 2010-07-19
athenaharmony


fglrx doesn't support your card RS690M Radeon X1200 in Lucid, only in Hardy8.04.
The default OSS driver(radeon) is the correct driver for your card and compiz does work with it.
Something has borked your GLX(3D)

Sharky

---

### Post by saidbakr on 2010-08-14
Hi,

this is the output of lshw
```

*-display:0             
       description: VGA compatible controller
       product: RV350 AS [Radeon 9550]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:11 memory:d0000000-d7ffffff(prefetchable) ioport:9000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AS [Radeon 9550] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff(prefetchable) memory:e5010000-e501ffff


```

Today morning everything were perfect, I played with some installations for ati in synpatic and then the graphic cards becomes limited, I could not able to run visual effects, when I run live cd it works fine!

I need to know how to get video or graphics drivers and setting to their states after installtion of Ubuntu or at least at today's morning!

By the way, my graphic card is AGP RADEON 9550.

---

