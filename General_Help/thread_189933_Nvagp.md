---
title: "Nvagp"
date: 2006-06-05
forum: General Help
---

### Post by Blarion on 2006-06-05
I heard I can get better graphical performance by using NVAGP instead of AGPGART. How do I enable this? I tried using Option "NVAGP" "1" in my xorg.conf but then when I use cat /proc/driver/nvidia/agp/status it just says Status: disabled. Please give me a hand! Also, how do I enable fastwrites? I'm a newbie, so please, if you can, try to keep it simple. X.x

---

### Post by Blarion on 2006-06-05
Can someone please help? Please?

---

### Post by Jott on 2006-06-05
I've got the same issue.  Anyone got ideas? 

Thanks!

---

### Post by JoWilly on 2006-06-05
What is your MB chipset ?

NVAGP only supports these chipsets:

 Intel 440LX
    Intel 440BX
    Intel 440GX
    Intel 815 ("Solano")
    Intel 820 ("Camino")
    Intel 830M
    Intel 840 ("Carmel")
    Intel 845 ("Brookdale")
    Intel 845G
    Intel 850 ("Tehama")
    Intel 855 ("Odem")
    Intel 860 ("Colusa")
    Intel 865G ("Springdale")
    Intel 875P ("Canterwood")
    Intel E7205 ("Granite Bay")
    Intel E7505 ("Placer")
    AMD 751 ("Irongate")
    AMD 761 ("IGD4")
    AMD 762 ("IGD4 MP")
    AMD 8151 ("Lokar")
    VIA 8371
    VIA 82C694X
    VIA KT133
    VIA KT266
    VIA KT400
    VIA P4M266
    VIA P4M266A
    VIA P4X400
    VIA K8T800
    VIA K8N800
    VIA PT880
    VIA KT880
    RCC CNB20LE
    RCC 6585HE
    Micron SAMDDR ("Samurai")
    Micron SCIDDR ("Scimitar")
    NVIDIA nForce
    NVIDIA nForce2
    NVIDIA nForce3
    ALi 1621
    ALi 1631
    ALi 1647
    ALi 1651
    ALi 1671
    SiS 630
    SiS 633
    SiS 635
    SiS 645
    SiS 646
    SiS 648
    SiS 648FX
    SiS 650
    SiS 651
    SiS 655
    SiS 655FX
    SiS 661
    SiS 730
    SiS 733
    SiS 735
    SiS 745
    SiS 755
    ATI RS200M

Regarding fastwrites, this has been discussed many times. The search function is your friend ;)

---

### Post by gamma on 2006-06-05
NvAGP will only become enabled if AGPGART isn't compiled in the kernel. As soon as it detects AGPGART it assumes you want to disable AGP. You'll have to compile a custom kernel to get NvAGP working or find a way to disable the AGPGART module..

---

### Post by Blarion on 2006-06-06
Don't got one of those motherboards. I have a VIAP4M800/8237. Ah well.

---

### Post by denkedran on 2006-06-06
check which agp_moduleis loaded with
```
lsmod | grep agp
nvidia_agp              9116  1
agpgart                37072  2 nvidia,nvidia_agp

```


then blacklist this module.
```
sudo -s
echo "blacklist {insert here the name of ne module eg. nvidia_agp}" > /etc/modprobe.d/blacklist-agp
echo "blacklist agpgart" >> /etc/modprobe.d/blacklist-agp
```

that will prevent the modules to load on startup
when nvidia module (the graphic driver) will be loaded the agpport will not be occupied by the kernel build in module and the nvidia driver will claim it

good luck

---

### Post by Jott on 2006-06-06
That worked for me - thanks!

Blarion - there's a good guide to enableing fastwrites at [http://doc.gwos.org/index.php/Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing](http://doc.gwos.org/index.php/Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing)

if you're still looking for it.

---

### Post by gamma on 2006-06-07
Is there any reason you guys want to use NVagp? I thought it was recommended to use it only if you can't get AGPGART working.. Any idea if it works with hibernate?

EDIT/UPDATE: Oho, very cool, I can actually use hibernate now with AGP support. That was one of my biggest issues using nvidia when having my laptop in battery mode.

```
:~$ cat /proc/driver/nvidia/agp/*
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x1f000314
Host Bridge:     PCI device 8086:3580
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x00000314
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Enabled
```

---

### Post by Jott on 2006-06-07
I wanted to use it just because someone said that it gave the graphics a bit of a bost, and I can't resist messing with things.  Haven't tried the hibernate with it - I'll be psyched if that finally works.  Is there any reason why I shouldn't use it?

---

### Post by gamma on 2006-06-07
Well nvagp was designed to be used as a fallback if your motherboard doesn't support agpgart. I have heard people state that one is faster than the other, but it seems nobody can agree which offers better performance. I'd recommend using NvAGP though just for the fact hibernate works with the default Ubuntu kernel. I'll probably write a FAQ that expands this guide..

---

