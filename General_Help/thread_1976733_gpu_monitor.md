---
title: "gpu monitor?"
date: 2012-05-09
forum: General Help
---

### Post by CosmoBeep on 2012-05-09
Im wondering is  there a nvidia  gpu monitor for ubuntu/kubuntu?

---

### Post by zeljkojagust on 2012-05-09
You can get temperature and fan speed readouts with lm-sensors for certain gpu/chipset combinations.

---

### Post by CosmoBeep on 2012-05-09
well I can monitor temps from nvidia x server settings. I'm working with 3d so I need a gpu montor for load and memory usage.

---

### Post by zeljkojagust on 2012-05-09
You can check nvclock, it allows monitoring and overclocking of nVidia GPU's under linux.

---

### Post by CosmoBeep on 2012-05-09
it says it only supports  gt200 but ill give it a shot

thank you

---

### Post by pqwoerituytrueiwoq on 2012-05-09
you can use conky

if you need to do it by command line with nvidia
```
nvidia-settings -q GPUCoreTemp | sed 's/\: /\n/g;s/\./*°C/g' | head -3 | tail -1
```
i doubt it will work with SLI though

---

### Post by CosmoBeep on 2012-05-09
Thanks,I dont know how to work with  conky but i look into it

I am only running 1 gpu so no biggy if it dont work with sli

---

### Post by efflandt on 2012-05-09
In a terminal type: **apropos nvidia**

There is an app that comes with the nvidia drivers, but I forget what it is called (no PC with nvidia on me at the moment).  But what it can monitor or output depends upon what support it has for that specific card.  It could tell me quite a bit about my GT 220, but little about my GTX 550 Ti.

---

### Post by CosmoBeep on 2012-05-09
ok after  putting **apropos nvidia **in the terminal it gave me this.

alt-nvidia-current-settings (1) - configure the NVIDIA graphics driver
alt-nvidia-current-smi (1) - NVIDIA System Management Interface program
alt-nvidia-current-xconfig (1) - manipulate X configuration files for the NVI...
nouveau (4)          - NVIDIA video driver
nvidia-settings (1)  - configure the NVIDIA graphics driver
nvidia-smi (1)       - NVIDIA System Management Interface program
nvidia-xconfig (1)   - manipulate X configuration files for the NVIDIA driver

---

### Post by waperboy on 2012-05-18
> **CosmoBeep said:**
> ok after  putting **apropos nvidia **in the terminal it gave me this.

alt-nvidia-current-settings (1) - configure the NVIDIA graphics driver
alt-nvidia-current-smi (1) - NVIDIA System Management Interface program
alt-nvidia-current-xconfig (1) - manipulate X configuration files for the NVI...
nouveau (4)          - NVIDIA video driver
nvidia-settings (1)  - configure the NVIDIA graphics driver
nvidia-smi (1)       - NVIDIA System Management Interface program
nvidia-xconfig (1)   - manipulate X configuration files for the NVIDIA driver

nvidia-smi gives me info on a bunch of stuff - depending on what card you have I guess. I can see mem usage, but GPU usage says N/A for me.

---

