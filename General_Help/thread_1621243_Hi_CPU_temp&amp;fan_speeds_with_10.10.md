---
title: "Hi CPU temp&amp;fan speeds with 10.10"
date: 2010-11-14
forum: General Help
---

### Post by SpencerHolst on 2010-11-14
Hey there.
I've upgraded to Linux after ~15 years of Windows and I'm loving it so far. However, 10.10 drains my batteries and I am worried about wearing out my CPU.

Average working temperature of the laptop is DEFINITELY higher now compared to WinXP. I've read a couple of threads on the issue, tried a bunch of things but no result yet. I don't even know what exactly to tell you; basically laptop is hotter and CPU fan almost never runs at the lowest speeds.

My system is HP Compaq nc8430 with 2gigs of RAM, ATI Mobility Radeon X1600 with 256mb memory.
Ubuntu 10.10 32bit with GNOME ('Normal' visual effects, no Compiz)

Any comments-questions to proceed with?

---

### Post by Tesko Value on 2010-11-14
Hello, Yes I had exactly that issue when I switched, My laptop is prone to overheating even with XP. 

In 10.10 I think you'll find the easiest solution is to. 
right click the gnome panel,
add to panel,
select CPU Frequency scaling monitor,
do it again for every CPU you have (I need to do it twice for my dual core),
then right click the monitors and go to preferences to change target CPU
then you should be able to select speed and governors directly :D 
I think this should go some way to improving your battery life also. 

ps you might want a little temperature applet so you can see it working just to satisfy yourself.

---

### Post by SpencerHolst on 2010-11-15
Thanks for the quick reply. I did not know those applets. No help though.
Even when idle, after like 10 minutes fan starts to spin at moderate speeds.

Can that be GPU instead of CPU? How can I monitor my GPU's usage?

---

### Post by SpencerHolst on 2010-11-16
One quick question: Is 70 degrees Celsius an acceptable idle-ish temperature for CPU to run?
I have only Firefox running with two tabs (non-flash content) and my CPU's are like 65-70 degrees, fan spins at a medium speed..

---

### Post by Tesko Value on 2010-11-17
Er.. 70 is pretty high. Thats the idle temperature I was getting when I first started using. So what I do now is have 2 cpu frequency scaler applets for each core and set them both to 800mhz which is fine for most things. I'm getting around 50 degrees when idle and 60 - 66 when its working hard. You said you tried that and it doesn't do anything? 
do you have scaling capability on your cpu I wonder?

I would personally think its the cpu thats the main culprit for these high temperatures. I'm not an expert but that seems more likely than the gpu.
I haven't got anything for gpu monitoring myself, but theres loads of sensor applets out there maybe one does that I'm not sure.

---

### Post by SpencerHolst on 2010-11-21
Thanks Tesko Value. It seems I have only you to get help!

Yup, my system seems to have CPU scaling capability. I checked from here after reading your post:

[http://*************/hub/Ubuntu--CPU-Scaling--Battery-life-and-You](http://*************/hub/Ubuntu--CPU-Scaling--Battery-life-and-You)

I am now using my laptop with the batteries removed.. :/
When on full batteries, after 10 idle minutes, WinXP gave an estimate of 3 hours before the batteries run out. When I first installed Ubuntu, the estimate was 2 hours. Now that I am using Maverick Meerkat for like less than 2 months, the same estimate came down to 1.20 hours. I am pretty much sure the problem here is damaging my batteries.

Edit: Forum rules do not let me let you know how I am proceeding. The link the script has cencored was the first one when I googled "cpu scaling".

---

### Post by Tesko Value on 2010-11-21
Thats the only way I know to get my cpu heat down mate sorry. Shame it seems to be caning your battery. 

Just to make sure please forgive me but it is easily overlooked, Did you for definite assign a different cpu core eg (CPU 0, CPU 1 etc) in each of your gnome panel applets? just in case you didn't its likely one or more of your cores is still running flat out.

My battery is pretty much dead anyway, I have to keep it plugged in but to be fair it was heading that way faster than I expected when I was running XP. They all go eventually.
I'm also running an HP Compaq so maybe that may have something to do with it. Like I said I'm no expert.

Incidentally that link isn't really relevant to 10.10 in the past it was needed but they are just there from the start so theres no need to sudo dpkg-reconfigure gnome-applets or anything you just right click the top panel and add to panel.

Ive looked into this a bit and I found a load of people with the same  problems. the solutions always ended up changing the cpu governors from  the terminal. these applets I think automate that for you so I'm not sure  if theres any other way. 

Anyone else know any crazy Linux magic to help this guy? 
 **

---

### Post by SpencerHolst on 2010-11-22
Big thanks for the effort mate. That's why I like this community.

Yeah, both my CPU cores are addressed properly, double checked. The scheme I choose is "conservative" and when idle, they run at 1ghz, which is the slowest clock speed allowed for my system.

I guess I will try to accept it as it is. Winter is ahead on this hemisphere, I may have a use for hi temperatures on my laptop! :)

---

### Post by Tesko Value on 2010-11-23
No worries.
Damn! yeah or you could sit outside with it to keep it cool. hope you find a better solution.

---

