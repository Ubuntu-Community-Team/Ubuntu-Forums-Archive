---
title: "About the drivers(nvidia)"
date: 2012-06-20
forum: General Help
---

### Post by xSadoro on 2012-06-20
Hi ,I recently installed ubuntu 12.04 and activated the nvidia graphics drivers from system settings but under system settings -> details -> graphics its like i hadnt any drivers installed , it says Unknown on drivers , so are my drivers installed , or not ?

Thanks for your help :KS

---

### Post by HiImTye on 2012-06-20
it won't show in 'graphics' you need to use the nVidia tool 'nVidia X Server Settings'

---

### Post by xSadoro on 2012-06-20
Umm if that so this is the information given by nvidia x server settings :

Operating system :          Linux x86
NVIDIA Driver Version :  295.40

GPU: GeForce 7300 LE

Memory: 512 MB
Memory Interface: 64-bit (someone please explain this)                

Now my question is , are the drivers correctly installed ? If so why i play Neverwinter nights in such low fps ? :(
EDIT: Please dont hate me , its fixed now , i dont even know...but its fixed , thanks for the anwer HilmTye , now im experiencing hungs up :( but i think that has something to do with my hardware , it might be broken...

---

### Post by prismctg on 2012-06-20
I m facing same problem in 12.04 ; Donn't know y !!

---

### Post by xSadoro on 2012-06-20
What problem about ,the hungs up ? ..Just now i was ...surfing the internet, and it was like a flash light or something and the comp frpze :( and the same happened to me while in neverwinter nights,but it was random , idk...

P.S:I still want to know if i have the best drivers installed

---

### Post by jmfal on 2012-06-20
In a terminal run:

```
 lspci -v    
```
 
 This will list all of your devices and  modules(drivers) for each device.

---

### Post by xSadoro on 2012-06-20
This is what I got: 

01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Device 2208
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cd000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at ccfe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb

Obviously beside other things

EDIT : Freezings/Hangs Up are getting annoying by now , I need help here , My comp even freeze for using firefox....

P.S.: I found out I have the xserver-xorg-video-nouveau ... Is this a driver ? Is this the one im supposed to have installeD?

P.S2: I think this only happens when the current version of the drivers is activated :(

---

