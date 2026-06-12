---
title: "What happens if i disable a video driver??"
date: 2010-10-07
forum: General Help
---

### Post by Gordonisnz on 2010-10-07
3D-accelerated proprietary graphics driver for NVIDIA cards.

Video card causing trouble - PC heats up & shuts down.


If I disable the driver - will PC go back to 'regular' graphics ?

Or will I need to physically open Pc & remove the card (Will get a friend to help).

---

### Post by FahadMKS on 2010-10-07
Most probably it should work.
Please check if your processor is good enough to support the graphics driver.
May be it might be the Processor that heats up.

---

### Post by sikander3786 on 2010-10-07
If you disable the drivers, I assume propritary drivers in this case, you'll be reverted to the open source drivers already present in the install, and still you'll have display on the same graphics card.

If you want to revert to the motherboard integrated graphics controller, uninstall the proprietary drivers from System > Administration > Hardware Drivers, remove the Graphics Card and connect your monitor to the motherboard.

If the PC is heating up, it might be worth to remove the graphics card and check. Still more worthy if you check the processor temperatures, motherboard temperatures, dust obstructing the air ducts, processor fan speed (or even if it is operating or not), loose heatsink/processor connection etc.

---

### Post by Mark Phelps on 2010-10-07
Removing your video card will remove one source of heat generation, but unless you've got a really high-end card and you're overclocking the GPU like crazy, I find it hard to believe that it's generating enough heat to crash your PC.

---

### Post by Wtower on 2010-10-07
> **Mark Phelps said:**
> Removing your video card will remove one source of heat generation, but unless you've got a really high-end card and you're overclocking the GPU like crazy, I find it hard to believe that it's generating enough heat to crash your PC.

Actually I had the luck to experience this with an ATI 4800 series and old version drivers on vista. After a lot of hours looking around, I realised that activating the 2nd display would bring the temp up to 70+C (the driver displayed the temp with a nice gauge graphic with 10-degree steps up to 70C). Eventually the system came to a halt. I would otherwise have shared the same opinion, now i might give it a probability.

Regards

---

### Post by TBABill on 2010-10-07
What is the cause of the higher heat? Most people experience it under heavy graphics and/or CPU loads. Flash is a big culprit. 
 
One thing you can do to bring heat down a bit is enable CPU frequency scaling. It won't impact your GPU getting hot if it is an app causing that, but it will help reduce heat coming off the CPU itself to at least minimize its contribution to machine heat. Simple to do...right click the top panel, click add to panel and select CPU frequency scaling applet. Set it to ondemand and you're set. This won't solve your immediate problem but maybe help reduce heat while you work on it.

---

