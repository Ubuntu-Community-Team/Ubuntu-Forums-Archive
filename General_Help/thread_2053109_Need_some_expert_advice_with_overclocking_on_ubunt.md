---
title: "Need some expert advice with overclocking on ubuntu"
date: 2012-09-04
forum: General Help
---

### Post by cannon_dt on 2012-09-04
Hi,
I have a desktop setup running ubuntu 12.04. It has a asus m4a785td-v evo mobo with a phenom ii x2 550 BE processor.
Recently I found that it being a BE processor I could unlock the 2 cores and make it a quad core - it does work and machine does boot into ubuntu. However I have to do some stress testing to check the stability of the new cores and there in starts my question. 
I intend to run mprime and I will monitor temps etc. For monitoring temps I am going to use gkrell and it works ok. I do have another thread ([http://ubuntuforums.org/showthread.php?t=2051243](http://ubuntuforums.org/showthread.php?t=2051243)) where I could use some more help :)
Now I wanted to monitor the ram frequency (I have corsair 4 gb 1333 MHz right now). So for that I thought cpufreq is the applet to use and I got it installed but now I am more confused, here are my questions (please bear in mind I am only running dual core now all at stock settings):
1. What are the 4 values it gives - I have a 3.1, 2.4, 1.9 (all GHz) and 800 Mhz? Is it the max speed, core 1 speed, core 2 speed and BIOS frequency that is set?
2. If mu understanding above is right then I am worried about the 4th value - I went into my BIOS and changed the Memclockvalue (under DRAM configuration) from auto to 533 and I expected this to change to 1066 but it remained at 800 (which corresponds to a 400 setting in BIOS).
Now I am left wondering if ubuntu will ever respect the value set in the BIOS?
3. Is this the only tool to monitor the real time frequency? Also will the applet keep giving me current values as the mprime is running?
4. If ubuntu alreadu has a scheme like on-demand, performance etc, then how will BIOS settings take effect? Should I turn remove this cpu frequency thingie off (as mentioned here [http://ubuntuforums.org/showthread.php?t=799535](http://ubuntuforums.org/showthread.php?t=799535)) if I intend to overclock?

I know this is a lot of questions but I need help. My hyper 212 evo cooler and arctic silver 5 paste is on its way to me and I intend unlocking the cores and overclocking very soon. Please treat this as an urgent question and help. I got nowhere else to turn to.

Thanks,
Ananth

---

### Post by pqwoerituytrueiwoq on 2012-09-04
3.1, 2.4, 1.9 (all GHz) and 800 Mhz?
these are the clock speeds the cpu runs at it lowers the value during idle to save power
this has nothing to do with your ram

there is no guarantee your 2 locked cores will be stable, odds are higher you can get a triple core, best not to get hopes up too high
:lolflag:
this will monitor your cpu speed
```
while [ 1 ];do clear;cat /proc/cpuinfo  | grep MHz; sleep 0.2; done
```you can use conky and applets also

i had to set my cores to performance as mprime would not get them over 800MHz

---

### Post by cannon_dt on 2012-09-04
Thanks pqwoerituytrueiwoq
So the 533 I changed in my BIOS is actually taking effect? Those 4 values remain constant throughout - so how exactly does this constitute a monitoring tool? :D

What about the this governance thingie of cpufreq (performance, on-demand etc ) - do I need to worry about it while stress testing?

Will try out that cpu frequency script that you gave - so while doing my testing this can run on a terminal right?

My hopes are high - I unlocked all cores and did a prime test and I rebooted within 15 seconds but I did see gkrell reporting 69 degrees - so I assume that it is the temperature that is causing the reboot and hence the cooler / thermal compound. Is that not the right conclusion? (Please say it is and do not puncture my hopes :), just kidding!!)

---

### Post by pqwoerituytrueiwoq on 2012-09-04
my 212 evo keeps phenom II 965 at under 45C at stock settings (3.4Ghz quad core 95 watt)
fans are under 47% max speed
hope it fits in you case (don't cut the heat pipes to make it fit, cut a hole(s) in the side panel)
you can get 4 cores ant not have it it 70C and power-off
you just have to lower the clock speed

i think the 544 in you bios is for your ram, this is not relevant to overclocking the CPU

this is your ram speed
```
sudo dmidecode --type 17 | grep Speed
```empty slots are Unknown
since you have ddr3 1333 it should say 1333 or 667 depending on your motherboard
> What about the this governance thingie of cpufreq (performance,  on-demand etc ) - do I need to worry about it while stress testing?

Will try out that cpu frequency script that you gave - so while doing my testing this can run on a terminal right?
if my script i posted for your  terminal is saying 800Mhz instead of 3100Mhz while mprime is running a stress test then yes

---

### Post by cannon_dt on 2012-09-04
As per the specs from the 2 sites below (for the cabinet and cooler)
[http://www.coolermaster.in/product.php?product_id=6709](http://www.coolermaster.in/product.php?product_id=6709)
[http://www.coolermaster.com/product.php?product_id=30](http://www.coolermaster.com/product.php?product_id=30)
it should fit - I do have enough clearance, fingers crossed :)

I live in India - so my ambients are high and without ac my idles are around 42-44 - I hope the evo and as 5, can help bring it down by around 10 degress.

I will ignore the RAM thing for now and I get that last line - when I run mprime just on my dual core and stock setting in BIOS, I should reach 3100 right? Will check that and let you know.

One thing - I did not understand these 2 lines of yours:
you can get 4 cores ant not have it it 70C and power-off
you just have to lower the clock speed

Can you please elaborate?

Thanks for all the help

---

### Post by pqwoerituytrueiwoq on 2012-09-04
each core generates X degrees 
your stock speed is 3.1Ghz
if you under-clock to 1.8Ghz you should be able to enable all 4 cores and it not overheat, you trade clock speed for cores, at least till you get that HSF

"3100 right"
assuming stock cpu speed yes, if you overclock to 3.4Ghz then it is 3400Mhz
ambient temp is ~22C here

---

### Post by cannon_dt on 2012-09-04
If the entire purpose of this exercise is to gain performance benefits then what would you suggest:
oc to the max with dual cores
or
oc as much as possible with unlocked cores (if stable)

I am not going to attempt oc until I get the hyper 212 - so I would not be underclocking I guess :)

---

### Post by cannon_dt on 2012-09-04
One more thing sire!
Gkrell and the script you wrote are enough monitoring tools required right? Just wanted to make sure I have everything in place before I attempt this.

BTW - that script worked like a charm - put the governance back to 'on demand' and that script showed me 800 for both cpu. Then ran mprime on another terminal and both cpus shot to 3100 in a matter of seconds. So thats great then.

I have one more question - LAST ONE, I promise :) -
After unlocking core, what would you consider as the correct amount of time to run mprime to ensure that the cores are stable? Do we require hours, just wanted to know. Also after every cpu multiplier / cpu voltage bump (while overclocking) how much time would you recommend running mprime to conclude on the stability? 

Thanks a ton sir, you have been of immense help - very grateful

---

### Post by pqwoerituytrueiwoq on 2012-09-04
on an air cooler 15min will have your max temp, but i suggest googling that one
messing with the voltage is like playing with fire, don't touch it if you cant afford a new/replacement cpu (better safe than sorry)

---

### Post by cannon_dt on 2012-09-05
OK, thanks for all the help.
I intend to be as safe as I can, so I guess I should be okay. :)

---

### Post by Dr.Paneas on 2012-09-05
It's sad but true that there are no monitoring tools in Ubuntu and Linux in general. I would suggest your to drop down the memory frequency and try to find the highest FSB value of your motherboard. Them pick the sweet spot between CPU Freq and RAM Freq.

Currently I am writing my own monitoring tool called [uXray,]("https://github.com/ubuntuxtreme/uXray") though it's not good enough and it needs a loooot of improvement. 

There will be a guide soon at UbuntuXtreme, but for now I am giving exams to the university so can't help. I will come back at you when my exams over, as soon as 15 Sept.

Take care and be safe,
after all even a dead clock is right twice a day ;)

---

### Post by cannon_dt on 2012-09-05
Yeah - for now, I will stick to the freq monitoring script and gkrell for temps. 
I am sorry if this question is silly - but what relevance does the RAM frequency have in this whole process - oc is mostly the voltage / CPU multiplier(what you refer to as the FSB right?) bumping and adjusting - so why bring in the RAM frequency.

All the best for the exams, will give this a shot and I hope I dont have fried stuff when you get back to me :)

---

### Post by cannon_dt on 2012-09-09
pqwoerituytrueiwoq,
I have a small clarification.
I actually unlocked my cores and mprime ran for 8 hours and all was well.
I am now proceeding onto oc. I raised my multiplier to 17 which means I am running at 3.4GHz.
However when I run your script on a terminal while running mprime after the above BIOS change the speed reads 2400 MHz. Why is that so? Should it not read 3.4 GHz? Is it because it is now running 4 cores (when I ran dual, on running mprime the speed jumped to 3.1 GHz, so why not 3.4?)

Please help if you can.

Ananth

---

### Post by cannon_dt on 2012-09-09
Now I am just plain scared.
I am oc ing at 3.8 with voltage at auto and 30 minutes of prime runs fine. Temps max at 49 (this is probably not the actual core temp as unlocking cores does not show the temps - its probably around 4-5 degrees cooler - say 44-45). But the problem is the script reasing cpuinfo still shows only 2400 at max load (running prime).
I am wondering if I am really oc ing at all given that the speed still shows only 2.4 GHz.
Can someone really help?

BTW, voltage maxes at 1.34 V.

Please comment guys

Ananth

---

### Post by Epodx64 on 2012-09-09
If your new to overclocking I recommend reading some guides theres alot more involved then just increasing FSB and Ram speeds. here's a decent guide
[http://www.tomshardware.com/reviews/overclocking-guide-part-1,1379.html](http://www.tomshardware.com/reviews/overclocking-guide-part-1,1379.html)

---

### Post by cannon_dt on 2012-09-09
I have read a lot of guides including the ones specific for phenom ii x2 550 BE. I got my new cooler etc like I have said in this thread.
My only problem now is that even though my processor is overcloced to 3.8 GHz why does cpu info still keep saying 2.4 GHz? I am not able to understand that and hence I doubt if I am really getting that speed. The BIOS, under CPU information, clearly states 3.8 - so what am I missing?

---

### Post by Epodx64 on 2012-09-10
> **cannon_dt said:**
> I have read a lot of guides including the ones specific for phenom ii x2 550 BE. I got my new cooler etc like I have said in this thread.
My only problem now is that even though my processor is overcloced to 3.8 GHz why does cpu info still keep saying 2.4 GHz? I am not able to understand that and hence I doubt if I am really getting that speed. The BIOS, under CPU information, clearly states 3.8 - so what am I missing?

Do you have all the power saving features turned off? disable Cool & Quiet, AMD Cool Core, C1E state, and anything else that scales the processor

---

### Post by cannon_dt on 2012-09-10
Actually thats where I had screwed up. My C1E support was disabled but my Cool 'N' Quiet was on - disabling that seems to have resolved the problem. However I am not sure of the other options you refer to - I cannot seem to find that in the BIOS.

With just CnQ disabled, with the multiplier at 17, the script does report 3.4 GHz. So I think that was the problem though some people at overclock do not seem to agree with this. :(

FYI - my mobo is asus M4A785td-v evo, if you do know of any other setting I need to change, please do let me know

---

### Post by Epodx64 on 2012-09-10
> **cannon_dt said:**
> Actually thats where I had screwed up. My C1E support was disabled but my Cool 'N' Quiet was on - disabling that seems to have resolved the problem. However I am not sure of the other options you refer to - I cannot seem to find that in the BIOS.

With just CnQ disabled, with the multiplier at 17, the script does report 3.4 GHz. So I think that was the problem though some people at overclock do not seem to agree with this. :(

FYI - my mobo is asus M4A785td-v evo, if you do know of any other setting I need to change, please do let me know

Could be something bottlenecking it do you have anything like a thermal throttle setting? it's been awhile since I've overclocked an AMD (k8 athlon x2 6000+) and overclocking an Intel 2 Core is way different but check all your power settings whats your FSB to Ram ratio? It could even be a chipset problem
(for example my build right now is a Gigabyte G41MT-SP2T with a Intel 2 Core Duo E8400 The max multiplier on that board is 9 and stock its 9x333=3.00ghz
with a 1066 1:1 Ram ratio this board doesnt have NB voltage settings and the Ram divider has just six options over all 200mhz 266mhz 300mhz The absolute best I could do with 300mhz was 343x9=3.08 or something like that then I discovered a little trick if for some reason on these boards you increase the PCIe clock to 104mhz it gives you a slightly higher overclock upto 357*9=3232 and the ram is at like 1143mhz (its good ram though Coisar XMS3 DDR3 1333mhz/1066mhz) and I have the ram timings set to 8-8-8-24-1T That's seriously the best Overclock i've been able to manage on a G41 chipset a whole 232mhz and my ram is slightly overclocked to 1153 atleast it runs cool at idle its only 35c at load it hit a high of 38c anyway just thought i'd share this with you because you could have a chipset/processor wall

---

### Post by SlugSlug on 2012-09-10
Just a question.. do you actually see any difference between your standard clock speeds and OC speeds in your daily usage??

---

### Post by Epodx64 on 2012-09-10
> **SlugSlug said:**
> Just a question.. do you actually see any difference between your standard clock speeds and OC speeds in your daily usage??

At 3.2323 not really I was just hell bent on getting a G41 chipset to overclock higher then the 343 wall the 357 i hit next and literally nothing works G41's have everything tied into the FSB clock PCI,PCIe,etc... so there difficult to OC I was considering just putting mine back at stock because im a little bit worried having the PCIe at 104Mhz

---

### Post by cannon_dt on 2012-09-10
Epodx64,
I am sorry but most of what you said flew above my head :)

FSB stock for me is 200. I dont know how to find the fsb:ram ratio :(

Here continues my story:
After figuring out that CnQ was the problem, I disabled it. Since I could not get any turbo option I just did the cool and quiet disabling. Ran prime for around 30 minutes - it went through 2 full 11 and 12 test cycles with all workers up and running. Temperature of CPU once went to 50 but was hovering at 47-48 (ac running in the room !), voltage once went to 1.31 but was averaging at 1.27-1.28.

But - the speed reported was 3113.941.

Does look like Cool 'n' Quiet was responsible for throttling

Then I went ahead and increased the multiplier to 17 and when I ran prime everything just froze. I tried this twice and the same result - each time I had to hard boot.

All cores unlocked system seems stable.

So now either
1. I get the mutliplier down to 16 and see if it is the same result. Could this mean that I need to bump the voltage up - it is still set to AUTO.
or
2. Run prime for 8 hours again

The good part is that before I ran prime after bumping up multi to 17, I did a speed check and the script returned 3.4GHz. So it looks like Cool 'n' Quiet was indeed the throttling culprit.

What do you think?

---

### Post by Epodx64 on 2012-09-10
How good is your cooling? because higher vCore some where around 1.4 volts would probably help stabilize it but more volts means more heat if you have a good cooler and good airflow go ahead and bump up the voltage probably increase the ram voltage a little too do you know what your rams rated for? My corsair xms3 ddr3 are rated at 1.65v but I can keep them stable at 1066 8-8-8-24 at just 1.5v

---

### Post by cannon_dt on 2012-09-10
My cooling is good - I have anewly installed hyper 212 evo with arctic silver 5 paste - in fact that is what helped me unlock cores. Before that running prime would result in reboot in 10 seconds. After these installed I am able to get better temps.

Like I said the temp only once went to 50, otherwise it was hovering at 48 with volts at around 1.3

---

### Post by Epodx64 on 2012-09-10
48 c Isn't to bad you could probably push the vCore up little bit take to around 1.4v (probably don't wanna go over that) and get the best FSB speed that syncs with your ram speed for example on my board its 333*9 = 333 x2 *9 1066 1:1 fsb to ram ratio multiplier  I'd also say loosen up your ram timings abit so it can compensate for the higher clock rate take it up to like 9-9-9-24 or even 10-10-10-30 then bring it down after you have a stable OC take it down one at a time 9-10-10-30 9-9-10-28 9-9-9-24 until you hit a wall depending on your rams speed if its up to like 1066 8-8-8-24 would be pretty good oh yeah another thing once you hit your desired OC or the wall slower lower the Vcore until you can hit the lowest possible stable settings a 1.4vcore is gonna run hot and bump up NB too. same as the Vcore once you hit the wall or get your desired OC then lower the NB voltage & Ram voltage as well basically you want it to run as fast as possible as stable as possible at the lowest Voltage even if it's just a nominal decrease that runs stable like a minus 1.385 vs 1.400 it's worth it. one last thing try and keep your CPU around 55c under load tops anything higher then that you might run into trouble good luck if you wanna post a picture of your bios settings i can help you out with them

---

### Post by cannon_dt on 2012-09-11
Epodx64,
Like I said before, some of the things you say are going above my head.

Currently I realized that even if I bump my vcore up, gkrell reads only lower voltages. This I believe is due to the LLC setting in BIOS. I searched around a bit and realized that a 19% setting pretty much delivers what voltage I set (please see [http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/26327-asus-m4a785td-v-evo-m4a785td-m-evo-am3-motherboards-review-18.html](http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/26327-asus-m4a785td-v-evo-m4a785td-m-evo-am3-motherboards-review-18.html))
So currently I only manipulate 3 settings in my BIOS (other than the ones requires for unlocking cores - ACC, unleash mode etc)
1. CPU Frequency multiplier
2. CPU Over Voltage
3. LLC

Can you please tell me what you think and where I will get at with all this? Is it necessary to bring RAM into the picture as I thought BE phenom processors generally work well with just altering the above settings. Can you please be as clear as you can as I am not very experienced with all this and I am learning with every piece of advice/info I get?

Thanks

---

### Post by Dr.Paneas on 2012-09-14
Take a look at this guide about Intel Overclocking CPUs (Core i3/i5/i7) [http://ubuntuxtreme.com/opinions/basic-concepts-of-overclocking-intel-core-i3i5i7-cpus/](http://ubuntuxtreme.com/opinions/basic-concepts-of-overclocking-intel-core-i3i5i7-cpus/)

---

