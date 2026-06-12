---
title: "Installing second video card"
date: 2010-08-17
forum: General Help
---

### Post by xelasha on 2010-08-17
This would be the one thing that has always held me back from using Ubuntu as my main OS on my desktop. Now with Lucid Lynx in the picture I would really like to try again and get some answers this time around.

I have 2 GPUs in my system, a HD4870 and a HD4350. The HD4870 has a Benq 24" and a Dell 17" which are working fine in a multi-display desktop setting (No Xinerama) configured via CCC. 

On the HD4350 I have a single Samsung 17" which in CCC is listed as '[Unknown Display] Unknown adapter' and cannot be used. How can I get that working properly so I can configure it as an additional screen in this setup?

Also on a side note, I have a small problem with CCC. When I installed catalyst and drivers I configured my screen resolution and multi-display desktop, but every time I reboot my resolution for both screens is set to 1280x1024 and they are cloned. Why don't my settings save?

---

### Post by xelasha on 2010-08-18
*bump* jesus this thread is already on the ninth page. Seems like a lot of people need support.

This forum needs a few more sub-categories.

---

### Post by kmccmk9 on 2010-08-18
What happens when you go to System>>Preferences>>Monitors ?

---

### Post by xelasha on 2010-08-18
The two working monitors are available. The third is not there.

---

### Post by xelasha on 2010-08-18
*bump* And here is my Xorg.conf but it wouldn't help. It is default because my configurations don't seem to want to save to it! :(

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3200 1080
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

```

And my information the HD4870
```

  description: VGA compatible controller
                product: RV770 [Radeon HD 4870]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:32 memory:c0000000-cfffffff(prefetchable) memory:e7000000-e700ffff ioport:9000(size=256) memory:e6000000-e601ffff(prefetchable)

```
And my HD4350
```
       description: VGA compatible controller
                product: RV710 [Radeon HD 4350]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:16 memory:d0000000-dfffffff(prefetchable) memory:e5000000-e500ffff ioport:a000(size=256) memory:e4000000-e401ffff(prefetchable)

```

---

### Post by xelasha on 2010-08-18
*BUMP* I usually wouldn't do this on any other forum but threads get knocked back pretty quick here and I'm desperate to get this working.

---

### Post by xelasha on 2010-08-18
*bump*

---

### Post by kmccmk9 on 2010-08-18
I hear you I have to do the same thing on my thread. But yes thats weird. So it recognizes two but not three. And judging by what those logs say and what you said, your hardware can handle it. Maybe someone better with Linux Ubuntu can help here.

---

### Post by xelasha on 2010-08-19
Perfectly honest I don't think it's possible, to have it flawlessly running anyway. The best guide I could find was this 
[http://mugginix.com/articles/2009/Nov/12/Xinerama_Composite_Fail/](http://mugginix.com/articles/2009/Nov/12/Xinerama_Composite_Fail/)

And it says that if I'm dealing with ATI drivers that I am better off getting an eyefinity card. And that guide is based on a thread here on how to get a six monitor setup, I think that would qualify as someone with good knowledge of X. 

[http://www.youtube.com/watch?v=UhMErNsEoZw](http://www.youtube.com/watch?v=UhMErNsEoZw)

---

### Post by Mark Phelps on 2010-08-19
> **xelasha said:**
> ... This forum needs a few more sub-categories.

It already has them ... see Multimedia and Video ... which is the one you SHOULD have posted this thread in, instead of repeatedly bumping in this one.

---

### Post by xelasha on 2010-08-20
My apologizes. I mistook the category for Multimedia applications including video multimedia applications.

Please delete this thread as I have just made another in the appropriate category.

---

