---
title: "Is this a hardware or a software problem ?"
date: 2009-10-14
forum: General Help
---

### Post by emshains on 2009-10-14
My main computer recently broke down, so I got hold of another one. I took every single bit that might be useful from my old one and put it in the "new" one, so now it's specs are:
P4 presscot 3 ghz with h/t
1024 mb of ram (1 512 module was taken from the old one)
7300gt (taken from old one)
1 pata HDD (taken from old one)
2 sata HDDs
1 dvd-rw 
a pci wi-fi card (taken from the old one) 
a pci firewire card 
And a 400w power supply. 

I tried to run Test Drive Unlimited ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=7370](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7370)), and I thought it would run really smooth, judging from the review. I tried to use backbuffer instead of FBO, enabling/disabling gsls and all that other stuff I could find. And I tried to run it, but it crawled. I used both 190 and 185 drivers, but without success. 

Is this because I lack sufficient hardware to run the game? Is my power supply not strong enough ? Or am I doing something wrong. 
The reason I think it may be the power supply is because whenever I try to select something like "Fast" instead of normal in the bios, it can't boot up when I exit the settings, the monitor has no signal and my keyboard is not responsive. It's an MSI mother board, and in the bios, under "Voltage and frequency settings" I can choose between fast or normal system operation, or something like that. 
I ran it in 800x640 @ lowest settings possible and I still couldn't breach 30 fps. Here'š my output: 
```
fixme:win:EnumDisplayDevicesW ((null),0,0x20bed10,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x20bf42c,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
err:d3d:resource_init Out of adapter memory
fixme:d3d_texture:basetexture_generate_mipmaps (0x48b2ef8) : stub
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
fixme:d3d_surface:surface_load_ds_location No up to date depth stencil location
fixme:d3d_surface:surface_load_ds_location No up to date depth stencil location
```
This is what I get before it spams ```
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_R32_FLOAT

```
Those error messages are all spit out upon the launching of the game. The only error message during gameplay is this ```
fixme:d3d_surface:surface_load_ds_location No up to date depth stencil location
```

---

### Post by Giblet5 on 2009-10-14
Have you verified that you're using the nvidia driver?

```
nvidia-settings
```

Should bring up the specs/settings.

I multi-boot for games or buy those games that are available in native linux. I've never even tried it with Wine.

---

### Post by emshains on 2009-10-14
Well, I tinkered a bit with the driver settings. That didn't help. The only reason I don't dual-boot is because I have a ps3. I try to play this game just because it is not avaivable on the ps3. 

Another thing- when not at full load, working for about 24 hours, the cpu is around 80*C. Is that normal ? I know the Prescotts do heat up a lot, but 80 ? I could use this as my heater, or a fry my breakfast on it.

---

### Post by Giblet5 on 2009-10-14
> **emshains said:**
> Well, I tinkered a bit with the driver settings. That didn't help. The only reason I don't dual-boot is because I have a ps3. I try to play this game just because it is not avaivable on the ps3. 

Another thing- when not at full load, working for about 24 hours, it is around 80*C. Is that normal ? I know the Prescotts do heat up a lot, but 80 ? I could use this as my heater, or a fry my breakfast on it.

80C is high. My quad is running at 32C.

Stop letting your cat sleep on the CPU fan? ;)

---

### Post by emshains on 2009-10-14
> **Giblet5 said:**
> 80C is high. My quad is running at 32C.

Stop letting your cat sleep on the CPU fan? ;)

My cat got already punished for chewing the cord of the earphones. I am planning on putting a bigger fan/heatsink today. But the case is ventilated quite good, there's an intake fan, and an exit fan- something I have never had :) While your quad is running @ 30-40, your quad is also made using a 65/45nm production process ( is that the real phrase ?)

---

### Post by Giblet5 on 2009-10-14
> **Giblet5 said:**
> 80C is high. My quad is running at 32C.

Stop letting your cat sleep on the CPU fan? ;)


Are you sure you installed the CPU fan correctly (clean off the goop or thermal tape, apply very thin coat of thermal grease, firmly seat the cooler against the core)?

At 80C, you're approaching the temp when the CPU will start throttling back in an attempt to cool itself...

---

### Post by emshains on 2009-10-14
> **Giblet5 said:**
> Are you sure you installed the CPU fan correctly (clean off the goop or thermal tape, apply very thin coat of thermal grease, firmly seat the cooler against the core)?

At 80C, you're approaching the temp when the CPU will start throttling back in an attempt to cool itself...

I didn't seat the fan myself. It was done about 3 years ago, but it wasn't used regularly. Anyways, I will get a new thermal paste today so I can attach the big heatsink I've got.

---

### Post by Giblet5 on 2009-10-14
> **emshains said:**
> My cat got already punished for chewing the cord of the earphones. I am planning on putting a bigger fan/heatsink today. But the case is ventilated quite good, there's an intake fan, and an exit fan- something I have never had :) While your quad is running @ 30-40, your quad is also made using a 65/45nm production process ( is that the real phrase ?)

My quad is water cooled. THAT's why it's 32C...

Yeah, I cheated.

You might wanna try downloading the [UnrealTournament 2004 demo]("http://www.unrealtournament2003.com/ut2004/downloads.html") for linux and see what your performance is like. That's a great test for 3D performance AND CPU stressing.

---

### Post by emshains on 2009-10-14
I was planning to use cpuburn from the reppos to test it, but I don't think it's useful to stress-test your cpu without a way to monitor it'š temperatur real-time. The way I got the figure 80* C, was rebooting into bios to check it. 

BTW, what model is your quad core ?

---

### Post by Giblet5 on 2009-10-14
> **emshains said:**
> I was planning to use cpuburn from the reppos to test it, but I don't think it's useful to stress-test your cpu without a way to monitor it'š temperatur real-time. The way I got the figure 80* C, was rebooting into bios to check it. 

BTW, what model is your quad core ?

QX9650 running at 3.4Ghz.

Pricey chip... My wife's running a Q6600 clocked at 3.4Ghz and it's just as fast on most things that don't cache so well.

---

