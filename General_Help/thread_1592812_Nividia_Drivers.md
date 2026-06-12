---
title: "Nividia Drivers"
date: 2010-10-10
forum: General Help
---

### Post by artin101 on 2010-10-10
Is It safe to use the Nividia drivers given by default if so which one should I use?

There is version 173
and There is a version that is recommended....
which one is better.

---

### Post by Finalfantasykid on 2010-10-10
173 is a legacy driver and should only be used by old cards.

Chances are yours will work much much better with the 'reccomended one' as it is a newer driver and will have better performance.

---

### Post by artin101 on 2010-10-11
but i tired it on 10.04 and it ended up giving my splash screen 10x zoomed for resolution
and the resolution was probably like 640x something

---

### Post by blfer on 2010-10-11
I have a Sony Vaio VPCF11KFX/B i7 Quad core intel CPU w/8GB of Ram and tried installing 10.04. Had to roll back to Karmic 9.04.. Not everything works on 9.04 either but it's way better than 10.04..

Would like to update to 10.10 but not willing to break the machine again unless I confirm that 10.10 works properly with the nvidia drivers for advanced graphics. Anyone got any info on this subject? Sure would appreciate it. Thanks in advance.[FONT=verdana]
[/FONT]

---

### Post by Elfy on 2010-10-11
Right - I have removed a few posts which were pointless, FUD or just plain against the CoC. 

@artin101 - you need to give more information - what would be really useful is to know which card you have. If you don't know then run this from a terminal 

```
lspci
```

@blfer - 10.10 worked fine for me with nvidia-current. That aside don't hijack threads start your own.

---

### Post by kumaryu on 2010-10-11
The driver you need depends on the card you have.

Once you know which card you have (as noted above, lspci at the terminal), a search on this forum should give you a better idea of any issues associated it.

Nvidia-173 is for the GeForce 5 FX series. It now works with 10.10.

Those cards requiring Nvidia-96 drivers may have issues with Xorg Xserver 1.9. The cards affected are:GeForce 4 MX, Quadro NVS, Quadro 4 Go, Quadro 2 Go, GeForce 4 Ti, GeForce 2, Quadro 2 MXR. All from a number of years ago.

---

