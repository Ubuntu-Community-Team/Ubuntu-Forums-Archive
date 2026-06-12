---
title: "Choppy effects on compiz"
date: 2010-03-02
forum: General Help
---

### Post by Irti on 2010-03-02
Hi.. I am using 32 bit Karmic on my machine and I installed compiz and everything seems fine.... The problem is that when I enabled the wobbly effect on windows its very choppy....its irritating as I have a good configuration and I have installed the Nvidia 190.53 drivers too as explained on the website
My system specs are
AMD Athlon II core2duo
2 gb ddr2 ram
ASUS M2N4SLI
Nvidia 9500gt
2 x 500 gb hard drives

The thing is that the same wobbly effect works perfectly on my friend's pc whose config is much lower than mine..(1 gb ram and no graphics card i.e onboard intel graphics) so its definitely not a hardware issue....Any help plssssssssssss!!!!

---

### Post by Post Monkeh on 2010-03-02
> **Irti said:**
> Hi.. I am using 32 bit Karmic on my machine and I installed compiz and everything seems fine.... The problem is that when I enabled the wobbly effect on windows its very choppy....its irritating as I have a good configuration and I have installed the Nvidia 190.53 drivers too as explained on the website
My system specs are
AMD Athlon II core2duo
2 gb ddr2 ram
ASUS M2N4SLI
Nvidia 9500gt
2 x 500 gb hard drives

The thing is that the same wobbly effect works perfectly on my friend's pc whose config is much lower than mine..(1 gb ram and no graphics card i.e onboard intel graphics) so its definitely not a hardware issue....Any help plssssssssssss!!!!
i suspect it is a hardware issue.
compiz works great on my laptop with onboard intel graphics chip, yet it is quite laggy on my desktop with a radeon hd 3850, particularly when minimising and restoring windows.

apparantly the nvidia drivers are, in general, better, but they may still require some tweaking. i don't have an nvidia card, but don't rule out a hardware issue just yet.

---

### Post by Irti on 2010-03-02
hmmmm...allright so can i get any help on how to tweak my card to get the best results........

---

### Post by Irti on 2010-03-03
allright i just noticed...i turned the wobbly effects off and still when i move windows around the edges seem to get distorted...there is no lag but it seems as if the edges of the windows are being cut when i am moving them....i mean can't the new nvidia drivers even handle moving windows properly.???? i must be doing something wrong...could it be a problem with my screen ( benq 19 inch - 1366 x 768 @ 60 Hz) any one plss....need some help here

---

### Post by Post Monkeh on 2010-03-03
if i were you i'd ask an admin to move this into the hardware or multimedia sections, i doubt it's an actual problem with your hardware, just the way it's set up

---

### Post by Irti on 2010-03-03
allright.....any admin viewing this plss shift this thread to the hardware section .....and someone plsss give me an answer if you know how to solve this

---

### Post by Irti on 2010-03-03
Please don't let this thread go stale... i really do need some help...Plsss shift this thread to the hardware section or should i just post another one over there??????

---

### Post by hvbakel on 2010-03-03
The edge distortion is called tearing and can be avoided by enabling vsync. If you haven't done so already, install compizconfig-settings-manager, and after you started it, go to the "general" panel and under the tab "display settings" enable the checkbox "sync to vblank". Since you have an nvidia card, you might also want to set the refresh rate to 60Hz manually, and disable "detect refresh rate" (autodetection doesn't work that great with nvidia cards).

As a final performance tip, you might want to look into setting powermizer to the highest performance setting. The following link has instructions how to go about this: [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)

---

### Post by Irti on 2010-03-06
sorry i couldn't reply earlier...got a bit busy wit other things so couldn't get time to fix this..thanks a lot..it worked marvellously.....it was exactly what you said...and enabling vsync and using powermizer fixed it completely

---

