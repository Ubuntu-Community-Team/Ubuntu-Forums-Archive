---
title: "Changed BIOS battery, error message, now sluggish"
date: 2010-04-28
forum: General Help
---

### Post by Edgar Humbert on 2010-04-28
My PC is quite old. I don't expect much from it but a short time ago it refused to boot up. I opened her up, cleaned out all the dust and replaced the BIOS battery. It booted up properly afterwards but with an error message that went as such...

> Ubuntu running on low graphics mode.

Screen, graphics card and input device settings could not be detected correctly. Need to configure these yourself.

Keep in mind that I'm only somewhat competent with computers. I don't really know what that means. Though my PC now boots and functions in a fairly usable manner, it runs very sluggishly. There is much lag and I can no longer play music or stream video. Also, the fan was at once very noisy. Much more noisy than before. I suppose I must configure my settings but I do not know how. I wasn't able to find any information elsewhere. Admittedly, my search may have been cursory but I didn't even know what I should be looking for.

I was considering reinstalling with small linux distribution since xubuntu, 8:10 Intrepid I think, may be pushing my aging machine to the limit. I don't know if that will fix the problems however. 

Advice?

---

### Post by harrismh777 on 2010-04-28
Greetings from Minnesota,
  The symptoms you are experiencing are very common and usually easy to deal with. So be patient, but don't reload xubuntu!  Not yet anyways.
   When the BIOS CMOS battery goes dead your machine loses its cmos settings, some of which will either keep the machine from booting normally, or will make the machine run very slowly... for instance, your agp aperture setting, PCI settings, agp fast write, etc etc... all motherboards are different.  
   So, you might want to boot into the BIOS and see if you have a "set default settings" or better "set optimal default settings" or something to that effect.  This will get the cmos settings back *closer* to what they were before the battery died. Then you can tweek from there. Do you have the motherboard manual ?   If not, you can probably find it on-line... with tips about the various settings.
   About the noise. This is also normal for an old machine and easily fixed. What happens is that the fan (in the power supply) spins for a long time in one position, accumulating dusk on its blades... and aquiring wear on the bearings. When you tip the machine around to change the battery the dusk falls off the blades (unevenly). Now, with the wear on the bearing, the blades spin out-of-round and whalla... noise... my own machine did this today and for the very same reason!   Take the power supply out of the machine (carefully) and open it if possible (power cord unplugged) and gently brush (small camel hair) the dusk off the blades and vacuum the insides. Clean both sidesd of the blades,,, but you will notice that one side is dirtier.  Re-assemble.   Noise will be gone, or greatly reduced.
regards,8-)

---

### Post by Edgar Humbert on 2010-04-29
Thank you for the input. I'll try that out and see what happens.

The only problem with the fan seems to be that it runs at full speed *all* the time. Right from startup it goes at full speed, going from silent to loud in a few seconds. I assume that will stop when the settings are as they were prior.

---

