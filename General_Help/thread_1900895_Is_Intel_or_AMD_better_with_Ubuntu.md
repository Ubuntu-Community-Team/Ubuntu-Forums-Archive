---
title: "Is Intel or AMD better with Ubuntu?"
date: 2011-12-27
forum: General Help
---

### Post by Spaceman9 on 2011-12-27
Should I buy a laptop with an Intel cpu or one with an AMD cpu for Ubuntu? They are both 64 bit chips.

Thanks for your help.

---

### Post by mcduck on 2011-12-27
Both work just as fine with Ubuntu. Which one's a better buy depends on how much money you are planning to spend, what kind of prices they have, and what kind of tasks you plan to do with your computer.

In general AMD can give you more physical cores for the same money, giving a noticeable performance boost on tasks that efficiently use multiple threads. On the other hand Intel has more powerful cores, so you'll get better performance on single-threaded tasks. So one could say if you do 3D or video rendering or similar work, AMD might be a better value for your money, while for most "normal" desktop usage Intel would be a better option. However the price points of each processor model can mix things up a bit.

If I had to give a simple (although not always correct) answer, I'd say if you aren't sure, get the Intel one. If you are working with things where AMD excells you probably already know it.

---

### Post by collisionystm on 2011-12-27
> **Spaceman9 said:**
> Should I buy a laptop with an Intel cpu or one with an AMD cpu for Ubuntu? They are both 64 bit chips.

Thanks for your help.


Go with Intel if you want to deal with less B.S. 

AMD chips usually come with AMD graphics. Amd graphics are a nightmare with Ubuntu.

Intel however is 100% compatible. Intel also runs colder so your laptop wont be burning up your lap

---

### Post by sammiev on 2011-12-27
It seems I had always better luck with Intel. Then again, that's me. :)

---

### Post by Spaceman9 on 2011-12-27
Thanks very much for your help guys. I'll get the Acer with Intel cpu.

---

### Post by xyzzyman on 2011-12-27
> **collisionystm said:**
> Go with Intel if you want to deal with less B.S. 

AMD chips usually come with AMD graphics. Amd graphics are a nightmare with Ubuntu.

Intel however is 100% compatible. Intel also runs colder so your laptop wont be burning up your lap

I currently use an Intel CPU, but to be fair your statement isn't currently true, especially about being 100% compatible. Sandy Bridge based notebooks especially are running very hot for alot people and battery life is much worse than under Windows (Some people cut in half). It looks like a fix for the majority of the issues have been finally found for this regression but it won't be in the mainline kernel until 3.3 but Ubuntu is backporting it at least for Precise, and their is a backport PPA for oneiric with 3.2 kernel with the aspm fix.

The Intel based notebooks with Optimus technology with switchable video cards are also just as tricky to get working as the AMD A8 line with their GPU on the CPU. 

So mcduck is who I'd have to agree with. What are you looking to do with the system? Such as what things do you want to do past just browsing the internet, send email, etc. Depending on that we can give you tips on what things other than brand of CPU to look for. How long you plan on keeping it along with how much you want to spend come into play. If you keep things until they die and aren't worth upgrading means you may want to get alot more RAM than you would think you'd even use now as down the road it winds up getting used. If you're a new phone every year and a new laptop every 2 years then no point in over spending necessarily.

---

### Post by xyzzyman on 2011-12-27
> **Spaceman9 said:**
> Thanks very much for your help guys. I'll get the Acer with Intel cpu.

What's the model? I'll take a quick look at the full specs and see if there is anything that might be a red flag. Try to provide the full model # (Example: Aspire 6930-1130) Not just the first # as that covers alot of models, the second is the sub #. Being Acer they use pretty generic parts so most likely no problems (I worked repairing their return they got from retailers for 2 years, and I currently am on my Acer Aspire laptop that's a few years old but still running strong. I no longer have brand loyalty. lol)

Another thing is even if you plan on ever using Windows: MAKE YOUR RECOVERY DISKS FIRST THING. If it gives you the option to also burn a seperate disk with just applications and drivers, do that also. Better to be safe then sorry for whatever reason and try to get the discs from Acer.

---

### Post by collisionystm on 2011-12-27
> **xyzzyman said:**
> I currently use an Intel CPU, but to be fair your statement isn't currently true, especially about being 100% compatible. Sandy Bridge based notebooks especially are running very hot for alot people and battery life is much worse than under Windows (Some people cut in half). It looks like a fix for the majority of the issues have been finally found for this regression but it won't be in the mainline kernel until 3.3 but Ubuntu is backporting it at least for Precise, and their is a backport PPA for oneiric with 3.2 kernel with the aspm fix.

The Intel based notebooks with Optimus technology with switchable video cards are also just as tricky to get working as the AMD A8 line with their GPU on the CPU. 

So mcduck is who I'd have to agree with. What are you looking to do with the system? Such as what things do you want to do past just browsing the internet, send email, etc. Depending on that we can give you tips on what things other than brand of CPU to look for. How long you plan on keeping it along with how much you want to spend come into play. If you keep things until they die and aren't worth upgrading means you may want to get alot more RAM than you would think you'd even use now as down the road it winds up getting used. If you're a new phone every year and a new laptop every 2 years then no point in over spending necessarily.


I have a Dell Vostro 3750 with an i3 Sandy Bridge and it works 100%. The battery life is actually longer than on Windows.

Either way, Intel still blows away AMD .

If you do decide to do AMD, 

make sure you install 

fglrx-updates from the terminal

then install compiz-config-settings-manager

run it, click on OpenGL and disable Sync to Vblank, set texture filter to fast, log out and back on. Open catalyst control and enable tear free.
That is the only way at the moment to get the best performance out of a radeon HD card which i am sure you will get with an AMD chipped laptop.

---

