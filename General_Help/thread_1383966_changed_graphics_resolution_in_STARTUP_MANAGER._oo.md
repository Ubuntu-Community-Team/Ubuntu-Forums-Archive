---
title: "changed graphics resolution in STARTUP MANAGER. ooops!!"
date: 2010-01-17
forum: General Help
---

### Post by benrufus on 2010-01-17
Hi

I just stupidly changed my graphics resolution in System - Preferences - Startup Manager, now i dont get a login window or anything just a black screen. I also disabled the splash but i assume this just gets rid of the ubuntu loading line thingy?  any help would be much appreciated......

the weird thing is that the resolution was set to 640x800 or something like that in the Startup Manager as default and the laptom im using (an old Toshiba Amilo P4) supports 1024x768. the System - Preferences - Display menu wouldnt let me change any display settings which is why i was messing about here. I havent got any backed up x org file and only a live usb of super os/ubuntu - no cd or floppy drive. Please please help.

---

### Post by benrufus on 2010-01-20
ok so i managed to sort it myself. at the boot up grub i pressed escape and booted using another kernel. Then i went SYSTEM - ADMINISTRATION - STARTUP MANAGER and then in the advanced tab restored original settings. Hope this can help anyone else with the same problem.

---

### Post by n0dix on 2010-01-20
The problem is solved?? If it is please add the SOLVED tag to the title. ;)

---

### Post by wojox on 2010-01-20
What kind of graphics card or chip are you using?

---

### Post by synapsys on 2010-01-20
> **benrufus said:**
> ok so i managed to sort it myself. at the boot up grub i pressed escape and booted using another kernel. Then i went SYSTEM - ADMINISTRATION - STARTUP MANAGER and then in the advanced tab restored original settings. Hope this can help anyone else with the same problem.

This is exactly why we tell people to keep at least 2 kernels in their boot menu.

---

### Post by n0dix on 2010-01-20
> **synapsys said:**
> This is exactly why we tell people to keep at least 2 kernels in their boot menu.

Did not know that!

---

### Post by benrufus on 2010-01-21
It was only by luck that i had the other kernel! which is great - why is that? sorry i am still learning ubuntu. also any idea why i dont have the option to change the resolution in my display preferences. Im not sure what graphics chip i have. if you tell me the code to enter in the terminal i can check it. Thanks

---

### Post by plucky on 2010-01-21
> Im not sure what graphics chip i have. if you tell me the code to enter in the terminal i can check it.

```
sudo lshw -C display
```

> It was only by luck that i had the other kernel! which is great - why is that?


The linux kernel image is upgraded for security and bug fixes.

It is always a good idea to keep at least 1 extra kernel,just in case something breaks the current kernel.

Good Luck

---

### Post by benrufus on 2010-01-21
now that i have the option of 2 kernels will it always be the case? it was very handy for me this time!

here is the output i get for my graphics stuff


  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0



im sorry i know this is unrelated and this post is getting a bit messy but i have another question. my flash is jerky and unwatchable in full screen, for example in you tube. also facebook poker dosent work unless i use seamonkey. im trying to get my friends to switch from windows but this is proving a real stumbling block. Thanks for your help.

---

