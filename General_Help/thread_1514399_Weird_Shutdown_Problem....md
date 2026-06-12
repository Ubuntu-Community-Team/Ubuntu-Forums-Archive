---
title: "Weird Shutdown Problem..."
date: 2010-06-20
forum: General Help
---

### Post by Lovecannon on 2010-06-20
Okay, last night I when I shut down my PC, it shut down normally, and power was cut to whole system, now out of the blue, when I went to shut it down this evening, as soon as ubuntu shut down, the pc kicked back on, and the fan started running at 100%, and the screen went black, and just stayed there, and whenever I hit the power button, it went back to the loading screen and loaded into grub and ubuntu. And every time now, it does the same thing, even when I hold the power button to shut off the PC, it does not power off, it just simply exits Ubuntu and goes black (but it isn't hibernating). I have never seen this glitch before, and I have no idea what is causing it, because nothing has changed on my system for the last few days. Its not a major problem, but now I have turn off the power at the wall in order to shut the computer down completely.

Does anyone know how to fix this or what is causing this?

---

### Post by dim3000 on 2010-06-20
Hold the power button for 10 seconds, if it powers back on check your BIOS settings and hardware.

---

### Post by Lovecannon on 2010-06-21
> **dim3000 said:**
> Hold the power button for 10 seconds, if it powers back on check your BIOS settings and hardware.

I said it powers on fine... and I said that holding the power button does nothing but send it into that state.. I looked at my BIOS, and theres nothing wrong with the hardware that I can see, all my hard drives work and so do the cd drives, it just doesnt fully shut down :\

---

### Post by dim3000 on 2010-06-21
If you held the power button for 10 full seconds when shutting down, then it is almost definitely a hardware problem.

---

### Post by wojox on 2010-06-21
Try right clicking the panel and +Add the Shut Down Applet.

---

### Post by Lovecannon on 2010-06-21
> **dim3000 said:**
> If you held the power button for 10 full seconds when shutting down, then it is almost definitely a hardware problem.

Yeah I figured it was probably a hardware problem, but I dont see what kind of hardware failure would only cause that problem, and no others... seriously it hasnt affected anything else, it just doesnt fully shut down now, its more of an annoyance than anything.. but I would like to fix it if possible, so if you have any idea what could be causing it that would be sweet.

---

### Post by dim3000 on 2010-06-21
> **Lovecannon said:**
> Yeah I figured it was probably a hardware problem, but I dont see what kind of hardware failure would only cause that problem, and no others... seriously it hasnt affected anything else, it just doesnt fully shut down now, its more of an annoyance than anything.. but I would like to fix it if possible, so if you have any idea what could be causing it that would be sweet.

BTW what's the computer model and also you might wanna check the BIOS for anything like: Wake on LAN, Wake on Ring, etc... and disable it.

---

### Post by Lovecannon on 2010-06-21
> **dim3000 said:**
> BTW what's the computer model and also you might wanna check the BIOS for anything like: Wake on LAN, Wake on Ring, etc... and disable it.

Well its a custom build. It has a dual core 2.4ghz Intel processor, 4 gigs of RAM, Nvidia 7900GS Gfx card, and 4 gigs of RAM. Im running Lucid Lynx x64, and I have 3 hard drives (each 320gb). Oh btw the motherboard is an Nvidia nForce (I forget which model off-hand). I dont know why it would be the BIOS, because I havent changed any settings, this problem came out of the blue. But Ill double check to make sure. :\

---

### Post by Lovecannon on 2010-06-21
Anyone have any suggestions?

---

### Post by happyhamster on 2010-06-21
Perhaps some weird shorting issue? Try cleaning the inside of the case (dust). And especially check the reset button pins on the motherboard for weirdness. Also, if you happen to have a spare power unit, try booting/shutting down with that one attached instead of the current one.

---

### Post by amjjawad on 2011-01-11
It's weird indeed. Too bad that there's no update about this issue. The OP did not post anything else.

I had a Shutdown Problem for many years, 3 or maybe 4. I could not shut  down my PC unless I hold the power button for few seconds. So, it was  NOT that worse.

What really fixed the issue (NO MATTER WHAT OS I have/had) was to wipe  the whole HDD and install a fresh copy of Ubuntu 10.04 and it's 32-bit.
My PC is: P4 3GHz - 2GB RAM - 500G HDD SATA + 40G HDD IDE.

I hope to hear back from the OP whether this case has been solved or not :)

---

