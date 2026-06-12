---
title: "Screen Flickering: HP DV6000 series laptop"
date: 2009-08-15
forum: General Help
---

### Post by Bucky Ball on 2009-08-15
Hi all,

Anyone got any ideas? I am figuring this is somehow connected to faulty hardware but ...

My laptop dual-boots vista and Ubuntu. Only really use Ubuntu and over the last few days, my laptop screen has been starting to flicker after about five minutes. From my research, I am starting to figure that might be the backlight. I can't really see how this could be related to software.

So, had some friends over today. Before they got here I booted up my laptop and into Vista. Left it sitting here for around ten hours now and not a flicker in sight. Am typing this from Vista and the machine is acting perfectly normally.

Could this be a software thing? As I say, hard to imagine, but the machine is at the point where Ubuntu boot is pointless. Vista runs fine though? What gives???

8.04 LTS
HP Pavillion DV6000 series (AMD Turion 64x2)

This machine is really reliable and no probs because it has to be that way (production, not a testing machine). This is odd.

---

### Post by Screwdriver0815 on 2009-08-15
does it have an NVidia graphics card?

If yes: its a bug in the graphics driver but it can be solved

---

### Post by matthewbpt on 2009-08-15
I think like the user above its an nVidia problem, I had a similar problem with my dv9000, something to do with the graphics card constanly switching between high and low power mode and causing the screen to flicker every so often. I fixed it with this script added to the ~/bin folder and added to the gnome startup scripts. I can't remember where I got the script from.

```
#!/bin/bash

while true; do
    if on_ac_power; then
        nice /usr/bin/nvidia-settings -q all > /dev/null
    fi
    sleep 25;
done
```

---

### Post by Screwdriver0815 on 2009-08-15
I have another solution which works sometimes but not always:

open the files /etc/modprobe.d/nvidia-kernel-nkc and /etc/modprobe.d/nvidia

```
sudo gedit /etc/modprobe.d/nvidia-kernel-nkc
```

```
sudo gedit /etc/modprobe.d/nvidia
```

and paste the following to their respective end

options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"

save and done...

but as mentioned this solution works not always. For example, when you scroll through websites in Firefox quite fast, the screen starts to flicker again.

I am now trying the suggestion of matthewbpt... so far it works good! Thanks!

---

### Post by jerrrys on 2009-08-15
for what its worth, about a week ago i installed 804 on my (wife's) dv6000 and to date have no issues with it.
and yes we have the same processor (1.7 clock) and nvidia.  nvidia has needed no special attention and has worked out of the box. one idea, disengage power management and see what happens...

---

### Post by Bucky Ball on 2009-08-15
Thanks for all the suggestions people, I will start to investigate tomorrow (2am here).

If it is a problem/bug with the nvidia driver (yes, nvidia graphics) why would it show up out of the blue now, a year later? (I have been running 8.04 for about a year.)

As for power management, I don't use any. This machine is ALWAYS plugged into a wall socket. Don't even use a screensaver. Never use it on batteries as doesn't leave the house (well, two or three times in a year and a half).

The machine has been sitting here for hours now in Vista and not a peep so I am reasonably convinced this is software problem now (which is a good thing!).

---

### Post by Bucky Ball on 2009-08-16
Hope I'm not speaking too soon but have been using machine today and this seems to have fixed it ...

In Power Management I have unchecked 'Dim display when idle' and set 'Put screen to sleep when idle for ...' to never. It was set to 12 minutes for some reason, about the amount of time before it was starting the flickering.

No problems so far. Fingers crossed at this end. Thanks for the suggestions.

---

### Post by Bucky Ball on 2009-08-16
I take that back. The screen just died totally. Now the machine boots up and sits there with a black screen. Not a flicker, no boot menu, nothing. 

This doesn't sound good. Time for a new screen, damn. Why can't these things happen in the holidays when I've got time to fix 'em rather than mid-semester when I'm flat out? Silly question ... ;-)

---

### Post by harecanada on 2009-08-16
Hey matthewbpt I'm having this flicker problem too. How do I add this script that you mention?
harecanada

---

### Post by Bucky Ball on 2009-08-18
Update on my problem: ***If you own a HP computer and you are having problems you should check their site immediately*** and go to the Support section for your model. A number of their models appear to have a known issue and HP are offering a Limited Warranty repair.

This applies in Australia and I would imagine for the rest of the world also. Check it out before you spend a heap getting it fixed.

* This might have started happening around the time I installed edubuntu-artwork and edubuntu-artwork-usplash. Wild one but I have uninstalled them as the computer actually booted after leaving it for a couple of days. 
* MatthewBPt; could you give more specific instructions as to how and where you are putting your script? ;-)

---

