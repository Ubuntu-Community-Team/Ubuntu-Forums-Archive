---
title: "lshw out put"
date: 2010-02-21
forum: General Help
---

### Post by Jenkins1 on 2010-02-21
Hi,

It would be a fantastic help if people could post the output of ```
lshw | grep -C display
```

and write what driver they are using open/propriety. (just incase its not stated obviously in the output)

I am trying to detect the display driver in use on different machines for a program I am helping with.

---

### Post by jocko on 2010-02-21
That command seems overly complicated for what you want it to do.
This does what you want:
```
lshw -C display
```And doesn't lshw always say which driver is in use?
But just to give you what you asked for (as you can see in the output I have a nvidia geforce 6200, using the proprietary driver):
```
jocko@jocko-desktop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: [COLOR=Blue]NV44A [GeForce 6200][/COLOR]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=[COLOR=Blue]nvidia[/COLOR] latency=248 maxlatency=1 mingnt=5
       resources: irq:19 memory:ca000000-caffffff memory:c0000000-c7ffffff(prefetchable) memory:cb000000-cbffffff memory:cc000000-cc01ffff(prefetchable)
```

---

### Post by Jenkins1 on 2010-02-21
Thanks jocko

> **jocko said:**
> And doesn't lshw always say which driver is in use?

when you use the open ati driver it doesn't say. Although I have only seen one lshw output so far.

---

### Post by Jenkins1 on 2010-02-22
bump, I could do with as many as possible please.

---

### Post by jmszr on 2010-02-22
Here you go:

```
jeff@jeff-desktop:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GeForce 6100 nForce 430
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

---

### Post by mechro on 2010-02-22
```
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200 Ultra]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
```

---

### Post by MooPi on 2010-02-22
*-display UNCLAIMED
       description: VGA compatible controller
       product: G84 [GeForce 8600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:e800(size=128) memory:feae0000-feafffff(prefetchable)

---

### Post by louieb on 2010-02-22
```

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e8000000-efffffff(prefetchable) ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)


```

---

### Post by Jenkins1 on 2010-02-23
Thanks everyone :) Please keep them coming.


> **louieb said:**
> ```

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e8000000-efffffff(prefetchable) ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)


```
Are you using the propriety ait dirver?

> **MooPi said:**
> *-display UNCLAIMED
       description: VGA compatible controller
       product: G84 [GeForce 8600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:e800(size=128) memory:feae0000-feafffff(prefetchable)

as far as i can tell you are not using the nvidia driver. What Driver are you using?

---

### Post by louieb on 2010-02-23
> Are you using the propriety ait dirver?

No. Running on an IBM T30 laptop running 10.4 alpha. Hardware driver not available through System>Administration>Hardware Drivers.  Been that way since V7.04 Feisty.

Heres one from an Intel desktop running Hardy   Nvidia  driver version 169.12

```

  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia


```

---

### Post by MooPi on 2010-02-23
> **Jenkins1 said:**
> Thanks everyone :) Please keep them coming.



Are you using the propriety ait dirver?



as far as i can tell you are not using the nvidia driver. What Driver are you using?
Open source what else :D, I don't require the overhead the nvidia driver requires because I use Openbox . Works wonderfully without the closed source binary.

---

### Post by cjhabs on 2010-02-23
sudo lshw -C display
```
 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:9110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d6500000-d65fffff
```

---

### Post by Jenkins1 on 2010-02-23
Thanks to all who have contributed so far. :) It has realy helped I am  all ready getting outputs that I hadn't come across.

---

### Post by pme 72 on 2010-02-23
*-display UNCLAIMED     
       description: VGA compatible controller
       product: RV710 [Radeon HD 4550]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff(prefetchable) memory:fdee0000-fdeeffff ioport:ee00(size=256) memory:fde00000-fde1ffff(prefetchable)

running default open source driver

---

### Post by Jenkins1 on 2010-02-25
Bump,

Please keep them coming I still need loads more.
Thanks

---

