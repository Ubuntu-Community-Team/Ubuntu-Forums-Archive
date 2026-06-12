---
title: "Why are 3d effects working without any graphics driver installed?"
date: 2012-05-05
forum: General Help
---

### Post by josephellengar on 2012-05-05
I was getting pretty frustrated with the Nvidia driver not working and how I kept being put in low-graphics mode. So I followed [these instructions]("http://ubuntuforums.org/showpost.php?p=9203671&postcount=1") up to step 5. That is, I blacklisted nouveau and all of those other drivers and completely uninstalled all of the Nvidia drivers, but did not install a new driver. Why are 3D effects and compiz still working? And why I am now able to use the most up to date kernel when I never could before? :confused:

---

### Post by josephellengar on 2012-05-06
bump

---

### Post by stinkeye on 2012-05-06
Check driver your using...
```
sudo lshw -c video
```

eg
```
glen@Precise:~$ sudo lshw -c video
[sudo] password for glen: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: **[COLOR="Red"]driver=nvidia[/COLOR]** latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```


Sure your still using compiz?
Are you being dropped back to the **Ubuntu 2d** session because you don't have the appropriate drivers?
```
echo $DESKTOP_SESSION
```

---

### Post by josephellengar on 2012-05-06
It says I'm using nouveau, but I thought that that didn't support 3D effects and all of the 3D compiz effects are still working.

EDIT: I'm just curious- not complaining about stuff that's working! :)

```


ross@ross-Laptop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 230M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:7000(size=128) memory:d3080000-d30fffff

```

---

### Post by stinkeye on 2012-05-06
> **josephellengar said:**
> It says I'm using nouveau, but I thought that that didn't support 3D effects and all of the 3D compiz effects are still working.

EDIT: I'm just curious- not complaining about stuff that's working! :)

```


ross@ross-Laptop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 230M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:7000(size=128) memory:d3080000-d30fffff

```

The nouveau driver works wth some nvidia cards and 3d.

---

