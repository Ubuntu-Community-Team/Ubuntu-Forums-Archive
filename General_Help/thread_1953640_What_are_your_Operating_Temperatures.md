---
title: "What are your Operating Temperatures"
date: 2012-04-06
forum: General Help
---

### Post by klingonklingoff on 2012-04-06
Hey guys what are your operating temperatures. If you can short list of hardware and SW. Myself:
AMD Phenom II x 6 1045T, Gigabyte MOBO, 450 W PSU, Midtower, stock cpu cooler, 1 120MM fan, 2 80mm fans with Ubuntu 11.10 and  windows vista on virtual box. my temps from psensor temp app is showing temp 1= 36 c, t2 = 38 c, t3 = 23 c. I think the BIOS temps actually show about 5c higher so im not sure which is correct. If you want just list your temps.

---

### Post by jonnyboysmithy on 2012-04-06
I got a i5 2410m 2.3ghz running at 51celsius (thats the temperature the fan kicks in). Also got the onboard integrated graphics turned on and being used.
This is on a laptop, dv6-6023TX.

---

### Post by QIII on 2012-04-06
Temps reported by the mobo are more likely to be correct and reports passed through software should be offset to match.  Trust the mobo temps you see in BIOS at idle.1

Those three temps are mobo temps and generally should represent system, socket and Northbridge.  You will have to consult your mobo documentation to determine the exact order.  Typically with Gigabyte, for instance, t2 is the socket temperature.

At 38 degrees at the socket, you are probably at 42-43 on the CPU.  As I said before, that temp is high for the load.  Running my 1100T Black at 100% load with my Noctua NH-D14, the highest I've seen is 47 degrees.  But that is also in a CM HAF X with all 4 200mm fans (2 in, 2 out), a 140mm exhaust and an extra custom 120mm intake fan.

Your 1055 should run cooler, so an idiotically over designed case is probably not in order for you.  But remember that 60 degrees is where your CPU flames out spectacularly.  You can't go as high as an Intel processor will let you.

You need to do four things:

1.  Find out which of those three temps is which.

2.  Install lm-sensors and do sensors-detect to load the K10temp module to get the on-die CPU temperature.

3.  Use a CPU load monitoring tool to monitor CPU load against temperature.

4.  Add 10 degrees to the CPU temperature because AMD processors return ridiculously low temps (below ambient).

Personally, I'd be concerned about those temps at that load.  Like I said before, the OEM HSF is a death sentence for that x6, especially if you do not have a very well ventilated case.  But I'm not saying to run around your house with your hair on fire right now.  Cause for rational concern.  Not cause for panic.

Again, I won't tell you how to spend your money.  I have it to burn, you probably don't.  But as a general rule, don't skimp on cooling.

When I get home I'll put a little load on that machine, let it run for a bit and post what my conky (scripted to offset temps) looks like.

---

### Post by Cheesemill on 2012-04-06
i3-540 OC'd @ 3.7 GHz with Gelid Tranquillo cooler, Antec 300 case with 4 x Antec TriCool 120mm fans (set to lowest speed).

On die CPU temp reported by lm-sensors is 20C idle, 35C during stress testing with mprime :)

---

### Post by QIII on 2012-04-06
Your CPU runs at ambient at idle?  ;)

---

### Post by Cheesemill on 2012-04-06
> **QIII said:**
> Your CPU runs at ambient at idle?  ;)

Not quite, I'm in the UK and it's pretty cold here at the moment.
The Gelid Tranquillo is a cracking cooler though :)

---

### Post by QIII on 2012-04-06
Even inside?  If I were to let it drop below 20 in the house, my wife would beat me with a wooden spoon.

Gelid makes good products.

---

### Post by Cheesemill on 2012-04-06
I'd rather put a jumper on and save the electricity bill for my toys (no mains gas where I live).

Anyway, enough off topic chat :KS

---

### Post by Yellow Pasque on 2012-04-06
I'm pretty sure others' temps will be irrelevant data to you, especially if they don't have the same CPU.

---

### Post by jonnyboysmithy on 2012-04-06
The i5 2.3ghz in my laptop runs at 70-75c when I convert a video. A bit hot!
EDIT: Everything is stock.

---

### Post by Bobhuber on 2012-04-06
> **klingonklingoff said:**
> Hey guys what are your operating temperatures. If you can short list of hardware and SW. Myself:
AMD Phenom II x 6 1045T, Gigabyte MOBO, 450 W PSU, Midtower, stock cpu cooler, 1 120MM fan, 2 80mm fans with Ubuntu 11.10 and  windows vista on virtual box. my temps from psensor temp app is showing temp 1= 36 c, t2 = 38 c, t3 = 23 c. I think the BIOS temps actually show about 5c higher so im not sure which is correct. If you want just list your temps.
Trust your Bios temps and not lm-sensors with the k10 chipset. I'm 80F (FL) room temp and idle around 40c with the latest 6/core Bulldoser and stock cooler (which on the new chip is quite impressive with heat pipes normally found on aftermarket coolers). 51c-53c with all six cranking. The temps you posted don't mean much without knowing what ambient (outside air) temps are. Your running a 95w processor so a good rule of thumb with correct airflow and stock cooling would be about 10c above ambient at idle. Just remember that the trick is not necessarily the number of fans but how you have them setup and airflow.

---

### Post by klingonklingoff on 2012-04-06
Well my room  temps are about 77 f. So if idle should be about 87 F thats about 30 c and mine is running 41 c about 10 c over which is about 20 f over. Thats quite significant. I know im kinda comparing apples and oranges if the cpu are not similar but maybe ill learn something. How are you guys keeping it only 10 degrees above room temps. Anything electrical is quite warm and cpus seem to run hot anyways. I have a 120 mm in the back of case one 80mm blowing above the cpu ( not the actual cpu fan) and one over the south bridge area. I have one more fan in the front of case blowing in but have not plugged it in yet as im not sure the cooling will be more than the current draw and the heat from it.

---

### Post by QIII on 2012-04-07
You paid good money for your machine, so take care of it.  I'm not  trying to alarm you or make you second guess your purchase.  You have to  keep to a budget and it sounds like you made a good purchase.  So don't  feel despondent.  (I wish they had better cooling options in those  deals.)  I'm just giving you 35 years of advice, OK?

You should always talk about computer temperatures in Celsius, not  Fahrenheit.  Room temperature is generally 20 -22C.  Ten degrees higher  than that is 30 - 32C.

The heat from that fan you don't want to plug is is negligible compared to the cooling effect you need inside the case.  Avoiding the use of a fan because you are worried about the very small amount of heat generated by a tiny motor is unwise.

You said your mobo is showing 5C higher than your software sensors.  Go  with that, as both I and the poster above said.  Thus, since you are  getting 38C from your software sensors, assume your temp is actually  43C.  That's the socket temperature.  CPU will be about 5C higher.  Make  that about 48C.  That's under what seems to me to be a low to moderate  load, from what you are describing.  Just rough figures. I think that is unreasonably high, so go back and check both your readings and my finger counting.

(K10temp is notorious for low readings as I, and the poster above said.  So as a rule of thumb I add 10C.)

A  direct comparison is a bit difficult, since I am running an 1100T Black  mildly overclocked the 3.4GHz inside a Cooler Master HAF X case with  2x200mm intakes, 2x200mm exhausts, a 140mm exhaust and a custom 120mm  intake mounted in 3 drive bays in the front.  That's a lot of air.  I'm  cooling with a Noctua NH-D14 (not pwm, unfortunately, so I have to set  the motherboard to control it by voltage.)

I'm idling right now at 29C on the CPU, 25C at the socket and 28C on the Northbridge.  Ambient is 19 - 20C

I  ran CentOS in a virtual machine and set a youtube video going.  That  got me up to 32C on the CPU at what is probably fairly close to the load  you described.

After that, I ran pi to 200,000,000 decimal  places on all six cores to keep the thing cranking at 100% for about 20  minutes.  It stayed steady at 47C when it settled.  That's what I always  see.

Make that, at full speed, about the same temperature as you are seeing at a light load with a stock HSF.

So,  what does that mean?  I think you are a little hotter than I would like  if I were you.  But that doesn't mean you need to have a fire  extinguisher at the ready when you push the power button.  You do,  however, need to be very careful with the loads you subject your CPU to  and for how long.

If a better HSF will break the budget, then at  least do this:  Put as many of the biggest fans as you can find on the  thing and strategically place them so that the airflow is as smooth as  possible and has a bottom to top bias to take advantage of what is known  as the "stack effect".  Hot air rises.  It's the same phenomenon that  causes a draft in the flue above a fireplace.  If your fans are low in  the front and high in back (but not top and bottom of the case) that is  fine.  Most mid cases are that way.  Make sure that you don't have exhaust fans blowing hot air out  where it will be drawn right back in by an intake fan.  Reduce turbulence in the case by  being extremely fastidious about cable management as you can.  Don't  leave a bunch of cables hanging loosely to cause turbulence.  (I'm not  going to argue the positive/negative pressure thing.  Just move air.)

With  the understanding that the software  sensors seem to read low, still use some  sort of on-screen temperature monitoring tool.  gkrellm is not great,  but it could be useful to you.  You can even offset the temps a bit to  adjust them to match your BIOS readings.

Start to get a good feel  for what activities and applications do what to your temperatures.   What combinations of things get you too close to that magical 60C  spontaneous combustion limit.  like i said, you can't do the 70C stuff you could with an Intel processor.

It might even be worth re-seating  your HSF, making sure you have the appropriate amount of thermal  compound.  I'd like to see an idle temperature around 32C at most in a  room with an ambient temperature of 20C.  With the stock HSF, you won't  get the cooling effect I'm getting under load, so you have to watch  what's going on at the top end.  Generally, idle temps are very close  between stock and high end coolers.

---

### Post by Cheesemill on 2012-04-07
> **QIII said:**
> It might even be worth re-seating  your HSF, making sure you have the appropriate amount of thermal  compound.

+1

You only need a thin, even layer of compound. Using too much can actually have a negative effect on your cooling. I usually use a blob about the size of a small pea and then either use a credit card to spread it out evenly, or you can just attach the cooler and let the mounting pressure do the job for you. I always use good quality compound as well.

Attached is a screenshot of my temps after 20 minutes of stress testing with mprime, specs are in my first post. I think I've got this cooling thing nailed, machine is still almost silent :)

---

### Post by Bobhuber on 2012-04-07
> **klingonklingoff said:**
> Well my room  temps are about 77 f. So if idle should be about 87 F thats about 30 c and mine is running 41 c about 10 c over which is about 20 f over. Thats quite significant. I know im kinda comparing apples and oranges if the cpu are not similar but maybe ill learn something. How are you guys keeping it only 10 degrees above room temps. Anything electrical is quite warm and cpus seem to run hot anyways. I have a 120 mm in the back of case one 80mm blowing above the cpu ( not the actual cpu fan) and one over the south bridge area. I have one more fan in the front of case blowing in but have not plugged it in yet as im not sure the cooling will be more than the current draw and the heat from it.
No +10c not farenheight. 77 f = 25c + 10c = 35c so your a bit warm at 41c no load.Not a big deal as long as you keep around 55c full load (all 6 cores ). Top fans should exhaust,  not push air in (heat rises) .Push on front,exhaust on rear and push for the side fans.You don't want positive pressure in the case. Your exhaust fan(s) should move slightly more air than the intake or at least be able to move the same amount .[FONT=Arial]I use (1) 120mm top and (1) 120mm side with the side fan running slower than the top. along with (1) 80mm front. This all depends on the size of the case. You also cant forget your power supply fan which also exhausts in the equation especially if it is not temperature controlled and runs all the time. A good way to tell is to remove the side cover on the case at idle and let the computer run a while. If your temperature drops significantly (more than 1 or 2 degrees) you have a cooling problem.Hope this all helps. Have fun ![/FONT]

---

