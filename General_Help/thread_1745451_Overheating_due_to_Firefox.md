---
title: "Overheating due to Firefox"
date: 2011-05-01
forum: General Help
---

### Post by jackn on 2011-05-01
My Asus laptop runs at above 60C at best. It often goes as high as 80C. Rarely, it will overshoot 90C and shut down automatically.

This is due to Firefox. 
I know this by CPU usage and because the heating depends on the number of open tabs - to cool the machine, I need to close some tabs. When I open more than, say, five, the machine overheats proportionately.

I'd add that since my recent upgrade to Natty (Firefox 4.0.1), the issue seems to have gotten worse.

Finally, it might be helpful to know that the overheating was even worse with Chromium, which I had to stop using for that reason.

I realize that hardware issues may be at stake here, too, but I'm wondering whether anything specific can be done to improve the software.
This doesn't happen on XP (dual boot).

This has been an issue for very long now (several versions / years, now running Natty).

Thanks.
jackn

---

### Post by lovinglinux on 2011-05-01
It is probably not the browser fault, but flash fault, which uses too much CPU.

Install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") extension, so it won't load unnecessary flash content. 

Also get [Bar Tab]("https://addons.mozilla.org/en-US/firefox/addon/bartab/") extension. It can be configured to unload tabs contents after some time of inactivity.

I also recommend [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/"), which will block lots of unnecessary stuff.

---

### Post by jackn on 2011-05-01
Indeed, I do notice greater overheating upon viewing Youtube pages than other, non-flash ones.
Have installed AdBlock and Flashblock, and will report.

Thank you kindly, lovinglinux.
jackn

---

### Post by Citizen247 on 2011-05-01
It's unlikely to be the software per-se, though I've heard that Natty is power hungry due to a regression in the 2.6.38 Kernel (which I'm generally not impressed with), which would seem to explain the issue getting worse, as I presume its a system throttling fault in the Kernel.

Anyway, I agree it's most likely Flash, the Linux implementation is particularly awful, it's not great anywhere, but on Linux it's particularly bad, lets hope HTML5 puts the double barrelled to it's head because we'll all be better off.

I'd suggest making sure that your air intakes are clear on the Laptop, as it shouldn't be over heating even if the CPU is running at max. Blow out the intakes with compressed air to get rid of dust and ensure they're unobstructed during use.

Good luck :)

---

### Post by jackn on 2011-05-02
I have tested the temperatures running under XP and running under Ubuntu with the same active software.

When Firefox isn't launched, the system hovers around 60C under both OS's.

When Firefox is running with fourteen Youtube tabs open, the system heats up to 70C under XP.
Under Ubuntu, on the other hand, it heats up to 86C.

Whether there is a hardware issue or not, and I believe there is, the results suggest that there is a software issue.

I have installed both AdBlock and  Flashbloc,
I find them unintrusive, even pleasnt (no rowdy stuff all over the place), and I find that things run at perhaps 5C lower, which is a useful cooling. 
It just about makes the difference between worrying about it all the time and just running a system on the hot side, but without immediate concerns.

Are these temperatures, as is my impression, indeed elevated?

Thank you, lovinglinux.

I'm not going to mark this as solved.
It isn't.
The helpful add-ons are symptomatic treatment, and there's still a fundamental issue that remains unknown and unresolved. See also the plethora of other threads on this.

Thanks for the input,
jackn

---

### Post by lovinglinux on 2011-05-02
> **jackn said:**
> When Firefox isn't launched, the system hovers around 60C under both OS's.

How many tabs open? Which kind of content on those tabs?

> **jackn said:**
> When Firefox is running with fourteen Youtube tabs open, the system heats up to 70C under XP.
Under Ubuntu, on the other hand, it heats up to 86C.

Fourteen YouTube tabs is way too much. I never open more than one YouTube tab at the same time, because it raises my Core2 Duo CPU usage to 30%. Flash has a serious problem in Linux. Basically, it can't use the xv output, which reduces CPU usage.

If you have a nVidia card that supports vdpau, then you could use such feature to reduce CPU usage.

---

### Post by no2498 on 2011-05-02
lovinglinux grease monkey helped my 2 computers with fire fox and opera

---

### Post by lovinglinux on 2011-05-02
> **no2498 said:**
> lovinglinux grease monkey helped my 2 computers with fire fox and opera

Which script?

---

### Post by no2498 on 2011-05-02
you got me on that 1 
all i did was install it

---

### Post by lovinglinux on 2011-05-02
> **no2498 said:**
> you got me on that 1 
all i did was install it

Well, greasemonkey by itself doesn't do anything, unless you install some scripts. So I wonder what exactly it helped?

---

### Post by no2498 on 2011-05-02
i did open fire fox is said no scripts loaded
it stopped my fans from running on tilt
im still on 10.04 btw

---

### Post by lovinglinux on 2011-05-02
> **no2498 said:**
> i did open fire fox is said no scripts loaded
it stopped my fans from running on tilt
im still on 10.04 btw

This is really unusual. I think is just a coincidence.

Remove or disable greasemonkey and see if the problem goes back.

---

### Post by jackn on 2011-05-02
> **lovinglinux said:**
> How many tabs open? Which kind of content on those tabs?




Fourteen YouTube tabs is way too much. I never open more than one YouTube tab at the same time, because it raises my Core2 Duo CPU usage to 30%. Flash has a serious problem in Linux. Basically, it can't use the xv output, which reduces CPU usage.

If you have a nVidia card that supports vdpau, then you could use such feature to reduce CPU usage.
Lovinglinux,
at 60C, no tabs, as FF isn't launched then. No browser.
That's what strikes me as too hot for a basic temperature. Is that right?

Of course fourteen tabs is too much. I was testing. 
The point is the considerable temperature difference between XP and Ubuntu

jackn

---

### Post by Shmantiv_Radio on 2011-05-02
I would also guess it's Flash. I've watched through quite a few TV series on YouTube recently and after a while Flash starts screwing up.

There's LightSpark that's an opensource version of Flash or something. Maybe give that a try.

---

### Post by Citizen247 on 2011-05-03
> **jackn said:**
> I have tested the temperatures running under XP and running under Ubuntu with the same active software.

When Firefox isn't launched, the system hovers around 60C under both OS's.

When Firefox is running with fourteen Youtube tabs open, the system heats up to 70C under XP.
Under Ubuntu, on the other hand, it heats up to 86C.

Whether there is a hardware issue or not, and I believe there is, the results suggest that there is a software issue.

It suggests that the software requires more CPU on Linux than on XP - which we've already ascertained. It's Flash, the fact that Flash is worse on Linux in every possible way than it is on Windows is well known.

What isn't proven is that your machine would be hotter under the same load in Linux than it is in XP, which would indicate a software problem with something other than Flash; you'd need to use stress testing software that places the same _system load_ (*not* the same _software_) on the machine under both Windows and Linux for that.
> **jackn said:**
> 
Are these temperatures, as is my impression, indeed elevated?

60c seems a lot. I'm running various desktop effects and a medium system load and my laptop is currently holding steady at around 50c, and even when the load peaks it doesn't go much over that.

Have you checked that the CPU/GPU air vents are clear?

---

### Post by jackn on 2011-05-03
Yes, I get your point about the difference between different CPU loads and different heating due to a given CPU load.

> **Citizen247 said:**
> 

Have you checked that the CPU/GPU air vents are clear?

No.
I'd like to, but I wouldn't know how. Other than gazing at the grille at the bottom of my laptop, what can I do?

Thanks, citizen.
jackn

---

### Post by lovinglinux on 2011-05-03
> **jackn said:**
> at 60C, no tabs, as FF isn't launched then. No browser.

Sorry. I totally misread the phrase :-)

> **jackn said:**
> That's what strikes me as too hot for a basic temperature. Is that right?

I don't think that 60C is too hot for a laptop.

Besides, raising the temperature to 86 while playing 14 YouTube videos is perfectly normal considering the quality of flash on Linux. It is expected that flash would cause more heat on Linux than on Windows.

---

### Post by jackn on 2011-05-04
I also took care of the hardware.
[This]("http://www.notebookreview.com/default.asp?newsID=4020") seemed like a good guide to cleaning the vents and fan.
I have always been wary of opening my laptop, a black box, as far as I was concerned.
It turned out not to bite, and I feel better about the whole thing.
jackn

---

### Post by jackn on 2011-05-08
OK, things are going very well.

Several days later, I now never see more than 65C.
Yet, I regularly run ten tabs or so.

All in all, and following the advice in this and other threads, I've used two FF add-ons (AdBlock and FlashBlock), I cleaned the fan and vents, and I propped up the far end of the laptop such that it's tilted to expose the vents.
I don't know what the relative contibution of the different measures is.

Thanks,
jackn

---

