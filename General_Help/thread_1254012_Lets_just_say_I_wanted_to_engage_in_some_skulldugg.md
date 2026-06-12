---
title: "Lets just say I wanted to engage in some skullduggery"
date: 2009-08-30
forum: General Help
---

### Post by sha.goyjo on 2009-08-30
Ok. Here's the situation. I have a computer. Which I own. No legal question. I want to fry it. It runs hot normally, but I want to know how to disable the automatic heat shut-off so that it melts itself into oblivion. How do I do it.

The machine is an hp tx200zcto tablet pc
The OS is ubuntu 9.04 Jaunty Jackalope

I'm assuming it's probably as simple as disabling a kernel module, but I just don't know which one.

So, tell me how to make my machine do this :popcorn:.

---

### Post by j7%&lt;RmUg on 2009-08-30
ok...WHY??

What could you possibly learn from overheating a computer??

It isnt even going to melt, plus not only is the automatic shutoff there for the computer, its also a safety mechanism so that you dont overheat your computer and start sniffing the burning metal fumes.

Honestly the things some people like to do for fun.

---

### Post by sha.goyjo on 2009-08-30
That's not the point. I should be able to do what I want with my PC. That's the whole entire point of the entire open source movement, no? 

If you don't know how, please don't answer. I know what it's going to do, I know why I want to do it. Does anybody know HOW.

---

### Post by mdurham on 2009-08-30
Just place flat on BBQ and when well done eat with lashings of chilli sauce

---

### Post by sha.goyjo on 2009-08-30
NOnono it is VERY important to the task at hand that the laptop die of "natural" causes. IE how do I make the system malfunction so that it overheats until it is nothing but a simple stone. Why is it that you guys think this is a joke. I'm asking a serious question here!

---

### Post by ppirilla on 2009-08-30
the issue is with the built-in mechanisms of the machine, moreso than with the operating system.

All computer motherboards are equipped with an automatic shutoff tied to the system temperature.  Most machines have this safety mechanism hardwired, so there is **no way** to override it though *any* operating system.

I don't know your particular system, so it may be one of the few exceptions.  If it is, chances are you can find out by digging through the BIOS.  If it's not, you might be able to find a way to physically override the system if you crack the case open.

Either way it's not in the realm of linux help.  sorry.

---

### Post by uylug on 2009-08-30
Seems to me you're trying to break into someone elses computer and make it burn, uh?

---

### Post by mdurham on 2009-08-30
You could try wrapping it in a blanket or similar, with it turned on of course. I don't think it will melt though.

---

### Post by sha.goyjo on 2009-08-30
> **uylug said:**
> Seems to me you're trying to break into someone elses computer and make it burn, uh?

LOL no, I'm actually doing research for an EXCEPTIONALLY paranoid client. I'm serious guys. Does nobody actually know how to do this? The kernel automatically kills the system at 90 degrees. How do I shut it off.

---

### Post by sha.goyjo on 2009-08-30
> **ppirilla said:**
> the issue is with the built-in mechanisms of the machine, moreso than with the operating system.

All computer motherboards are equipped with an automatic shutoff tied to the system temperature.  Most machines have this safety mechanism hardwired, so there is **no way** to override it though *any* operating system.

I don't know your particular system, so it may be one of the few exceptions.  If it is, chances are you can find out by digging through the BIOS.  If it's not, you might be able to find a way to physically override the system if you crack the case open.

Either way it's not in the realm of linux help.  sorry.

Naaah, I'm looking at my kernel logs and it's definitely the kernel sending the stop signal....I just can't figure out how to modify it so it won't.

---

### Post by sideaway on 2009-08-30
All it will do it just turn off and not turn back on again if you mange to continuously heat it up from the inside. You'll probably just crash it and it won't turn back on again, there's no 'melting ito oblivion'. 

Are you trying to cheat yourself into a free replacement? Because that's a real a**h*** thing to do. Unless of course it is actually faulty, but then you wouldn't need to fry it for a replacement.

However given the benefit of the doubt, you can just increase the voltage this will increase heat output, most automatic shutoffs however are bios based. There's no secret 'overheat protection' module, the manufacturers build them into the bios chips. So you can either actually heat it up (overclock it) continuously, and eventually the heat damage will take its toll and the machine will start to malfunction. Don't use external sources, unless you *want* to damage the outside...

EDIT, just read your two last posts. The kernel is shutting it off but it won't matter, the bios will kill power when it detects too higher temperatures anyway...

EDIT2: if you don't believe me, take the heatsink fan off, turn off all system fans (depending on the effectiveness of the heatsink) and leave the system in grub and it will shut off when it finally over heats.

---

### Post by sideaway on 2009-08-30
The other option is to just take all the heatsinks off... Lol. Hopefully the CPU will fry itself before the bios loads.

---

### Post by sha.goyjo on 2009-08-30
The bios on this laptop is REALLY closed. I can't manually alter chip voltage. In fact, I can't even get in. I would need some way to do it from userland. Do you know how?

The problem with this system is that it gets SO hot that it auto-offs after 5 minutes in performance mode. I'm not exaggerating. Before gnome can fully start, the machine crashes. I want to push it over the edge so it can never start again. As I said before, I'm doing this for research purposes only. I really do need an answer. When the machine gets too hot the system sends sigterm to all processes and a shutdown NOW order. I just want to inhibit that.

---

### Post by LzBy1 on 2009-08-30
I'll be watching the news tomorrow for house fires caused by overheated computers.

---

### Post by cariboo on 2009-08-30
Most auto shutdowns are controlled in the bios, is there no way to disable the over heating auto shutdwon?

---

### Post by Vince N on 2009-08-30
Pretty much the only thing you can do to make it die of natural causes is to abuse it either by over clocking, or deliberate sabotage of the systems heat control mechanisms as already explained.  There are several things built into the hardware for this purpose even if your in an OS with no thermal protection, the machines own inbuilt systems will try to keep it from frying unless you remove or disable them.

Frankly i'm  a little suspicious of your motives as well.  I'm sure there are better ways to obtain the data you require.

My laptop just died of natural causes and I can't afford to replace it for a while so if your that desperate to be rid of it I'll be happy to take it off your hands.  Hell take the HD out and keep it if your that paranoid about it.

---

### Post by savagenator on 2009-08-30
I think i can put in a few cents:

You have an HP, which most likely has in place a easy-to-use and simple BIOS, combined with an automatic shutoff hardcoded in, like other have said. I have a theory why you might think the kernel is shutting off the computer:

the computer sent the stop signal, like started "pressing" the power button for more than 10 seconds. This would start the shutdown process in linux if it is still booting up. 

Entirely possible, making it entirely impossible to do what you want with that computer. Try staying in the BIOS for a few minutes to see if it will shut off. Wrapped in heated blankets of course.

---

### Post by LzBy1 on 2009-08-30
The need for it to "die of natural causes" seems to me that there is a warranty that you want to cash in on but want it to look like you didn't violate the terms. Just saying....
:guitar:

---

### Post by fluffman86 on 2009-08-30
I seriously doubt the kernel is actively monitoring the system temperature looking to send a shutdown command.  It would, however, report a shutdown command sent by the BIOS, and it would appear in logs.

That said, I was working on a junker computer once and had to take off the heatsink to get to the RAM in a small case.  Plugged everything back in but forgot the heatsink.  I get the BIOS splash screen and within 5 seconds there's a blue spark, a loud pop, and some burning, seriously awful smelling plastic.  :)

---

### Post by mdurham on 2009-08-31
> **fluffman86 said:**
> I get the BIOS splash screen and within 5 seconds there's a blue spark, a loud pop, and some burning, seriously awful smelling plastic.  :)

As we all know, electronic devices run on smoke. You made the fatal mistake of letting it out. When this happens electronic devices generally cease to work correctly.

---

### Post by mdurham on 2009-08-31
> **aileen154 said:**
> Why is it that you guys think this is a joke. I'm asking a serious question here!
It's probably because it's a most unusual question and no one knows the answer.

---

### Post by mc4man on 2009-08-31
Considering it's a fairly new model of tablet pc you have no real chance of having the cpu 'fry' itself, even with an amd processor, which, in the past, could if the heatsink was removed. (intel's have thermal protection built-into the cpu, amd probably  does now also

The best way do get it to die a "natural' death, judging from some of the reviews, is just to keep on using it. ("runs hot, overheats, cheaply made"

Older amd's
[http://www.youtube.com/v/hsqGyLH-foQ&hl=en&fs=1](http://www.youtube.com/v/hsqGyLH-foQ&hl=en&fs=1)

> Main Entry: skul·dug·gery
: underhanded or unscrupulous behavior; also : a devious device or trick



---

### Post by lisati on 2009-08-31
> **mdurham said:**
> As we all know, electronic devices run on smoke. You made the fatal mistake of letting it out. When this happens electronic devices generally cease to work correctly.

Ah yes, I've been around long enough to know this but had forgotten. I once had a Z80-based machine which reminded me of this one day about 17 years ago by letting out some smoke of its own accord. My relationship with it was never the same again.....

---

### Post by rifak on 2009-08-31
well, if you are trying to achieve a natural death (and assuming it doesn't HAVE to be from overheating) then you can give the CPU an electric shock. open it up, get a 9V battery or any power source, and just shock the CPU...im guessing that will pretty much kill it with no real/visible damage

---

### Post by sha.goyjo on 2009-08-31
Thank you, those of you who have given serious replies. I have fully legal and legitimate reasons for doing this, however they are currently covered under a non-disclosure agreement, so I can't say what they are. I'll try the advice that has been given. Thank you very much for your time.

---

