---
title: "Overclocking; RAM upgrade."
date: 2010-05-03
forum: General Help
---

### Post by ubunterooster on 2010-05-03
I built a new system using my old RAM (2x1gb sticks @ 667mhz and 2x2gb sticks @ 533mhz), a nice SSD, a Gigabyte GA-MA785-GM-US2H motherboard, and a Athlon II x2 255 3.1Ghz AM3 (65 watts).

[color=blue]1, If I overclock the CPU, will I still be able to use the CPU Frequency Scaling Monitor to lower speed to 800mhz?

2, I have not found a site listing how far CPUs can be overclocked; do you know of any?[/color]

My motherboard lists support for DDR2 1200 OC Mhz memory modules but I have heard something about running in single channel mode if "maxing out on speed".

[color=blue]3, if I get 4 sticks of 2Gb DDR2 1200 OC Mhz RAM, do I get 8Gb of DDR2 1200 OC Mhz RAM running in dual-channel?[/color]

---

### Post by cascade9 on 2010-05-03
1- As far as I know, yes, even with overclocking you can use CPU Frequency Scaling. 

2- No single answer. Depends on how good your cooling is, what motherboard you have, how lucky you are with your chip, how game you are with the voltages, even if its 2 or 4 sticks of RAM, etc. Honestly- with stock cooling, and only a minor bump to the voltages, I would guess that 3.4Ghz will be as far as you can get. I've heard of that CPU going over 4GHz, with very good air cooling and more major voltage increases. 

3- I've heard..something...somewhere..about dropping back to single channel mode @ high RAM speeds. Cant recall where. You would be better off with DDR2 1200 @ 1066 and playing with the timings than @ 1200 in single channel mode IMO. 

BTW, 4 sticks can make a difference to how overclockable the system is, and how stable it will be for any given speed.

---

### Post by ubunterooster on 2010-05-03
2. Thanks, do you happen to know what voltages would go to make it 3.4?

3. Okay, should I get 4 sticks of 1200mhz and underclock to 1066, or get 4 sticks of 1066mhz RAM?

(I think my RAM is currently the weakest link)

---

### Post by 98cwitr on 2010-05-03
my BIOS will still read 3.6...Ubuntu only reads 3.2GHz w/ my e6750. Dont know which really holds true...maybe both haha :D

[http://ubuntuforums.org/showthread.php?t=1400474](http://ubuntuforums.org/showthread.php?t=1400474)

---

### Post by ubunterooster on 2010-05-03
The fact that further speeds make it unstable infers that it is running at 3.6

Have you tried entering "sudo powertop" in the terminal?

I think I'll order 1066mhz RAM tonight.

---

### Post by ubunterooster on 2010-05-03
Trying overclock I got a message that the CPU frequency could not be monitored. It was stable though. Anyway, I reset it to proper speeds and then realized that my motherboard does not support my RAMs low speeds and was  unintentionally overclocking the poor 533mhz budget modules. I odered 8GB of 1066mhz RAM. (It's expensive!) Anyway, just wanted to give anyone watching an update.

Thanks again, Cascade.

---

### Post by cascade9 on 2010-05-04
> **ubunterooster said:**
> 2. Thanks, do you happen to know what voltages would go to make it 3.4?

3. Okay, should I get 4 sticks of 1200mhz and underclock to 1066, or get 4 sticks of 1066mhz RAM?

(I think my RAM is currently the weakest link)

bacwards, because the 3rd is already done-

3- If you can get DDR1200, and its as cheap as DDR2 1066 with the same or better latency, then might as well....not that there will be a huge difference between 1200 and 1066. 

BTW, your motherboard overclocked the RAM without you doing anything? o.O Shouldnjt be that big a problem, DDR2 is pretty tough. 

3- From what I'm seeing, you shouldnt have to touch the voltage to get 3.4/3.6 (Anything over that will probably take a bit more voltage). I hadnt realised just how good the Ahhlon II X2 (and X3/X4) are at overclcocking. If buget wasnt a problem, I'd probably rather have a Phenom II with that nice chunk of L3 cache, but you cant always get waht you want. 

Anyway, heres a nice, small review on overclocking and power consumption for the Athlon II (+ Phenom II, Core2Duo Core2Quad, i3 and i7). Linked to the the Athlon II page- 

[http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking_3.html](http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking_3.html)

---

### Post by ubunterooster on 2010-05-04
> **cascade9 said:**
> BTW, your motherboard overclocked the RAM without you doing anything? o.O Yes, because it is unable to handle speeds lower than 667 it thought 667 is what my $40 of 4Gb 533mhz half-height RAM was> Shouldn't be that big a problem, DDR2 is pretty tough. Appearently, as it is alive now. ;) > From what I'm seeing, you shouldnt have to touch the voltage to get 3.4/3.6 (Anything over that will probably take a bit more voltage). I hadnt realised just how good the Ahhlon II X2 (and X3/X4) are at overclcocking. If buget wasnt a problem, I'd probably rather have a Phenom II with that nice chunk of L3 cache, but you cant always get waht you want.It's more power consumption than budget; if it's not transcoding it dosen't need to be above 800mhz at the time.> Anyway, heres a nice, small review on overclocking and power consumption for the Athlon II (+ Phenom II, Core2Duo Core2Quad, i3 and i7). Linked to the the Athlon II page [http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking_3.html](http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking_3.html)
That link is especially helpful, Cascade. :) Thank you.

---

### Post by cascade9 on 2010-05-05
> **ubunterooster said:**
>  It's more power consumption than budget; if it's not transcoding it dosen't need to be above 800mhz at the time.
That link is especially helpful, Cascade. :) Thank you.

There are a lot of Athlon II overclocking tests around, the only reason I posted that one is becuase I remembered that you were interested in power consumption. I'm glad it was interesting/useful for you. ;)

---

