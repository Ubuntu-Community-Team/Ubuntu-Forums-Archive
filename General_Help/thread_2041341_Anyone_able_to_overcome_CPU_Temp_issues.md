---
title: "Anyone able to overcome CPU Temp issues?"
date: 2012-08-12
forum: General Help
---

### Post by Petro Dawg on 2012-08-12
I run ubuntu12.04 and Win7 and noticed my laptop (Compaq Presario CQ64)  was getting way too hot in Ubuntu only.  I installed some sensor  software and found that my CPUs were running over 90 oC while gaming (Nexuiz or Supertuxcart),  and idled around 70.  

I installed Jupiter and now run in "Power Saving Mode".  The idle temp is now around 58 oC (much better), but quickly rises to about 70 oC when running only Firefox and gets up to 85 oC when gaming.  Also, gaming appears "glitchy" in power saving mode which kinda sucks.

I always set my laptop on hard flat surfaces as to not restrict airflow, and all the vents appear dust free.  I am considering purchasing a cooling pad (a base with fans for the laptop to sit on) to assist in cooling, but I'm not sure if they actually work that well.

I can give up gaming on Ubuntu if it means saving my CPU from damage, but I still think 70 degrees is still rather high for just web browsing.  Does anyone have any tips on what I should do next to keep my temperature down?   Would switching to a different browser make any difference?  Do cooling pads work?  Are the temperatures I'm running at actually too high or am I just over reacting?

Thanks in advance for any assistance.

---

### Post by HermanAB on 2012-08-12
Regularly clean the fluff out of the heat exchanger.

---

### Post by Petro Dawg on 2012-08-12
> **HermanAB said:**
> Regularly clean the fluff out of the heat exchanger.

The heat sink is clean and not the source of the issue.

Update:

Installed Google Chrome and it appears to run much cooler than firefox, at about 62 degrees.  Still heats up quickly to 74 degrees when playing youtube vids (80 degrees on full screen).

---

### Post by MutantJohn on 2012-08-12
I also noticed that Ubuntu made my CPU hot. I've also heard of a lot of other people with laptops experiencing similar issues. I upgraded the heatsink on my desktop so my issue is solved.

But aren't there laptop versions of Ubuntu? Isn't that what Lubuntu and Xubuntu or whatever they're called are for? Maybe Ubuntu was reserved for the desktops, whether it was intentional or not.

---

### Post by insane_alien on 2012-08-12
installing a cpu throttler such as cpufreq can help a lot.

I run it with the conservative govenor. meaning most of the time my cpu is clocked WAY down as low as it'll go (1.2GHz) and only brought up to its full 2.5GHz under full load. it helps the temperatures some.

but then, even without that I've seen lower temperatures than win7 pretty consistently until i ditched it. that may also be to do with the stripped down desktop i use. no fancy eyecandy at all.

---

### Post by flipper T on 2012-08-12
how old is your laptop?

i read the advice about clean the heat exchange for years & ignored it, until i opened up my laptop a few months ago (for the first time, its 6 years old) and it was like a woolly jumper in there.

i couldn't believe the amount of fluff. 

fluff free & now about 20 degrees cooler.

that said, ubuntu runs hotter than windows for me 2.

---

### Post by Petro Dawg on 2012-08-12
> **flipper T said:**
> how old is your laptop?

i read the advice about clean the heat exchange for years & ignored it, until i opened up my laptop a few months ago (for the first time, its 6 years old) and it was like a woolly jumper in there.

i couldn't believe the amount of fluff. 

fluff free & now about 20 degrees cooler.

that said, ubuntu runs hotter than windows for me 2.

My laptop is about 1.5 years old.  It doesn't get used often as my cell phone does most everything I need.  Most of the time my laptop is stored in a carrying case away from dust.

---

### Post by Petro Dawg on 2012-08-12
> **MutantJohn said:**
> I also noticed that Ubuntu made my CPU hot. I've also heard of a lot of other people with laptops experiencing similar issues. I upgraded the heatsink on my desktop so my issue is solved.

But aren't there laptop versions of Ubuntu? Isn't that what Lubuntu and Xubuntu or whatever they're called are for? Maybe Ubuntu was reserved for the desktops, whether it was intentional or not.

Didn't think about switching environments before.  I may consider running Xubuntu or maybe just Ubuntu 2D.  I'll look into that some more, thanks.

---

### Post by Petro Dawg on 2012-08-12
Update:

I installed Xfce desktop environment and also tried running in Ubuntu2D.  They both seem to reduce heat significantly and are about equally "cooler" than Unity3D.  I tried streaming youtube video and playing Nexuiz on both environments and my temperature is now topping out at around 70 degrees (which is about 20 degrees cooler than I started out at this morning).  I now web browse at around 56 degrees.  I believe these are fairly safe temps for my computer.

I'll probably stick with 2D Ubuntu for now, as I like Unity slightly better than Xfce.  

Thanks everyone for the suggestions.

---

### Post by GeneralCody on 2012-08-12
You should first of all vacuum your laptop after opening it, and you could use something like fancontrol to set the fans to blow max all the time.

[http://linux.die.net/man/8/fancontrol](http://linux.die.net/man/8/fancontrol)

---

### Post by Petro Dawg on 2012-08-15
I've been using Ubuntu2D on my laptop for several days now.  I kept it on and streamed music on it most of the day today while keeping an eye on the temp.  I also went back to firefox,  due to some performance issues I was having with Chrome (I'll be starting a new thread concerning that issue a little later).  My temp seems to be under control using Ubuntu2D, so I'm assuming my temp issues have something to do with 3D acceleration on my integrated graphics card. 




[IMG]http://www.flickr.com/photos/85387427@N08/7816197866/in/photostream/lightbox/[/IMG]

---

### Post by Petro Dawg on 2012-08-19
Update:
Took an old desktop computer (ran Win95 I think) and scraped off the  rubber feet off the bottom of it and installed them on my laptop.   Amazingly, after 14 years of being on that old computer, they were still  sticky enough that I could reattach them to the laptop without the use  of additional glue or anything, they just stuck (and stuck well).  The  feet are about 3 times thicker than the puny little rubber pads that  came installed on my laptop.  Temps dropped about another 7 degrees just  by lifting it up a little.

The difference in size can be seen in the picture below:

[IMG]http://farm9.staticflickr.com/8281/7816197866_72c672a405_n.jpg[/IMG]

---

### Post by TenPlus1 on 2012-08-19
Have you installed Nvidia's own binary driver or are you using the open-source one that Ubuntu installs for you ?  This will help in heat issues as the nvidia binary has powermizer control to slow down and speed up the GPU resulting in cooler running...

nvidia-current

---

### Post by Petro Dawg on 2012-08-19
My computer uses integrated ATI Mobility Radeon HD 4250 Graphics and AMD Athlon II Dual-Core Processor.  I don't think Nvidia drivers would work for me.  

I currently use the ATI/AMD proprietary FGLRX graphics drivers found with the "Additional Drivers" program.  I recently tried installing drivers directly downloaded from ATI website, but my system started running hot again, so I went back to the ones from provided through "Additional Drivers". 

I'm thinking for some reason my ATI integrated graphics chip is not being utilized and my CPUs are handling everything.  Not sure if that is true, or how I would go about checking that.

---

