---
title: "libgl1-mesa-dev is killing me..."
date: 2011-02-23
forum: General Help
---

### Post by TheBoxtheory on 2011-02-23
Hello there...well I have a rather weird problem...in 10.04

 So I downloaded these packages [Using sudo apt-get ] ...wanted to use  the opengl library for a game...

  ```
libgl1-mesa-dev libsdl1.2-dev libsdl-image1.2-dev
```

 After that though,I logged off[Back In]..and everything went wrong...extra desktop effects stopped working and If I try to enable them says "Desktop Effects could not be enabled "...awn doesn't seems to work properly...(Also had problems with sound through Chrome..although now everything is ok in this part )

 So I said OK,lets remove these evil things...and I did..[with both apt-get remove and through synaptic manager]...but for some reason these problems persist and still ruining my life...

 So If you know anything that can fix this...
Also I have to say that I'm a fairly noob in these Ubuntu things..

Thanks for your time..!! ;)

---

### Post by clhsharky on 2011-02-23
TheBoxtheory

Welcome to UF.

> So If you know anything that can fix this...
What's your video card?
And your driver?
> sudo lshw -C display

> ...wanted to use the opengl library for a game...
Ubuntu already uses opengl, there are fresher lib but need to know you HW and driver.

> After that though,I logged off[Back In]..and everything went wrong...extra desktop effects stopped working and If I try to enable them says "Desktop Effects could not be enabled "...awn doesn't seems to work properly...
May need to reconfigure your video
```
sudo dpkg-reconfigure xserver-xorg
```
logged off[Back In]


Sharky

---

### Post by TheBoxtheory on 2011-02-23
>  Welcome to UF. Thanks mate,appreciate your help...;)

>  What's your video card?
And your driver?         The terminal suspiciously says this : ```
 PCI (sysfs)  
          
                                *-display
                description: VGA compatible controller
                product: G80 [GeForce 8800 GTS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:9000(size=128) memory:df000000-df01ffff
 
```
            >  
May need to reconfigure your video ```
sudo dpkg-reconfigure xserver-xorg
```     That's exactly what I did..thanks for the help once again Everything is now back to normal...You saved me from format...:P

---

