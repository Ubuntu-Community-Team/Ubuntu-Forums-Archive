---
title: "Does adding a video card help for screen recording?"
date: 2010-10-05
forum: General Help
---

### Post by Ascenti0n on 2010-10-05
I have an HP PC (5 yrs old now) that relies on the build in Intel graphics support.

My PC has an spare AGP graphics slot and I was wondering if buying a cheap graphics card would help me produce better quality screen recordings (using GTK-recordmydesktop), without sending my CPU usage through the roof.

OR should I do screen recordings under WinXP?

---

### Post by searchfgold6789 on 2010-10-05
It will add to your vRAM, so yes I think it will help.

---

### Post by Ascenti0n on 2010-10-05
OK thanks. So are you saying it's the ram on the graphics card that makes the difference?

The only reason I ask, is that I remember reading various blog posts, which suggested that Ubuntu will (IN THE FUTURE) be able to use a the GPU of a graphics card to reliave the PC's own CPU cycles. so Ubuntu/Linux DOESN'T do that now?

---

### Post by Frogs Hair on 2010-10-05
Yes, you will be using the video card memory along with the dedicated video memory of the  system and that should greatly improve video performance .

---

### Post by searchfgold6789 on 2010-10-05
It's a work in progress, so I hear.

> However, GPU architecture is so varied and diverse ... I can't see unfied software bridging the gap anytime soon.
Unfortunately, GPU's have become warlords in their own right ... battling with each other aswell as the CPU.
It's akin to the competition between science and religion(s).
Perhaps OS/CPU/GPU players will gradually come home to roost. - delacroixp, Doom9's forum

I dunno about you guys but I think that would be really *really* cool!

---

### Post by cascade9 on 2010-10-05
> **Ascenti0n said:**
> OK thanks. So are you saying it's the ram on the graphics card that makes the difference?

The only reason I ask, is that I remember reading various blog posts, which suggested that Ubuntu will (IN THE FUTURE) be able to use a the GPU of a graphics card to reliave the PC's own CPU cycles. so Ubuntu/Linux DOESN'T do that now?

I doub that recordmydesktop will actually be writing to the video card RAM (VRAM is long gone now, BTW). If there is any advantage to using a video card for that, it would be the minor increase in system RAM (due to not having to 'share' the system RAM for the video card)

Using the GPU for CPU tasks? That would be via CUDA (nVidia) and Firestream (ATI). They arent going to by used for everything the CPU does- 

> **Current and future usages of CUDA architecture**

 
[LIST]
[*]Accelerated rendering of 3D graphics
[*][Real Time Cloth Simulation OptiTex.com]("http://www.optitex.com/images/downloads/Nvidia_CUDA_SS_OptiTex_FINAL.pdf") - Real Time Cloth Simulation
[*]Distributed Calculations, such as predicting the native conformation of [proteins]("http://en.wikipedia.org/wiki/Proteins")
[*]Medical analysis simulations, for example [virtual reality]("http://en.wikipedia.org/wiki/Virtual_reality") based on [CT]("http://en.wikipedia.org/wiki/X-ray_computed_tomography") and [MRI]("http://en.wikipedia.org/wiki/Magnetic_resonance_imaging") scan images.
[*]Physical simulations, in particular in [fluid dynamics]("http://en.wikipedia.org/wiki/Fluid_dynamics").
[*]Environment statistics
[*]Accelerated [encryption]("http://en.wikipedia.org/wiki/Encryption"), [decryption]("http://en.wikipedia.org/wiki/Decryption") and [compression]("http://en.wikipedia.org/wiki/Data_compression")
[*]Accelerated interconversion of video file formats
[*]Artificial intelligence
[/LIST]


[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

[http://en.wikipedia.org/wiki/AMD_FireStream](http://en.wikipedia.org/wiki/AMD_FireStream)

I dont know much about firestream, I know CUDA does install (from the repo) on some linux distros. How useful it is right, now, no idea there either.... 
  
Also, if you want to count VDPAU (nVidia vhardware video decoding) then ubuntu (and linux in general) already does "use a the GPU of a graphics card to relieve the PC's own CPU cycles"

---

