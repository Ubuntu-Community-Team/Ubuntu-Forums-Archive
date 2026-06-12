---
title: "how to disable action when battery power is critically low"
date: 2010-08-17
forum: General Help
---

### Post by pkhetan on 2010-08-17
Hi,

Under "Power Management Preferences" > "On Battery Power" > "When battery power is critically low" : We have several options : Suspend, Hibernate, Shutdown; but we don't have the do nothing option.

Does any one know if i can disable all these actions so the computer will do nothing when the battery power is critically low? May be by a terminal command?

Thanks

---

### Post by hansdown on 2010-08-17
Hi pkhetan.

In karmic, a popup asks if you wish to perform this operation, when the battery is low, and warns of low battery state..

I haven't tried lucid on this laptop yet, but it likely does something similar.

---

### Post by pkhetan on 2010-08-18
A popup appears when battery power is critically low. But, it's a warning-popup not a choice-popup.

---

### Post by mastablasta on 2010-08-18
you do know that taking power away while systenm is still running can critically damage the OS as well as computer hardware?

---

### Post by Grenage on 2010-08-18
It's probably do-able, but you'll likely end up both corrupting data and damaging the battery.

---

### Post by pkhetan on 2010-08-18
Then how to re-calibrate battery from time to time?

---

### Post by Grenage on 2010-08-18
Draining down to 5% is as far as I would want to go, draining the battery completely can ruin its maximum capacity.

---

### Post by pkhetan on 2010-08-18
> **Grenage said:**
> Draining down to 5% is as far as I would want to go, draining the battery completely can ruin its maximum capacity.

Yes. But the problem, if the battery need calibration, then the remaining 5% could mean in reality 50% (for example) because the OS reads a bad calibrated battery.

---

### Post by Grenage on 2010-08-18
When I've come across batteries that are so poorly calibrated, they have been beyond saving (if such things are ever possible).  Perhaps someone with more laptop experience will post here, and prove me wrong!

---

### Post by pizza-is-good on 2010-08-18
> **Grenage said:**
> Draining down to 5% is as far as I would want to go, draining the battery completely can ruin its maximum capacity.
NO. Please see below.

> **pkhetan said:**
> Yes. But the problem, if the battery need calibration, then the remaining 5% could mean in reality 50% (for example) because the OS reads a bad calibrated battery.
Yes, please see below.

> **Grenage said:**
> When I've come across batteries that are so poorly calibrated, they have been beyond saving (if such things are ever possible).  Perhaps someone with more laptop experience will post here, and prove me wrong!

Forcing charge in or out of the battery can permanently damage it yes. But, all batteries can be saved! Some require a lot of work and maybe even completely changing the chemicals, so you essentially get a new battery.
Also, it isn't really the miscalibration, but the cycles. Batteries that die do so because they have already gone through all of their cycles. Batteries are NOT meant to last forever. When they die, its likely because they have reached the end of their expected life, not because someone has fast charged them. (That is bad for batteries BTW, fast charging.)



I think you need a battery expert, not a laptop one, so here I go:

It all depends on the chemical make up of the battery. Lithium Ion batteries are by far one of the newest and best technologies available. You can drain them COMPLETELY, and still fully charge them without anything bad happening to it. You can also drain it 1% and charge it. It has no memory effect. Nickel batteries need to be drained completely to be able to charge them back up to its full capacity.

You can never really fully drain a computer battery. When your battery is 'critical', that only means that there is almost not enough voltage to power the computer, not that it is 'empty'. I have not checked, this is purely speculation. I think my laptop battery is 14.7 VDC. That being said, fully charged, it is probably at around 15.5 VDC. Fully drained may be at around 10 VDC. But that all depends on the computer. Some may require more voltage to operate than others. 

Volts are electromotive force, or 'juice'. Volts are the ones that cause things to work.
Contrary to common belief, you don't rid the battery of electricity, you use up the charge, which prevents it from working anymore, because there is a minimum amount of energy that is required for a certain task to be performed.

To fully drain a battery and get it to 0 Volts, you would need very sophisticated equipment, of just to leave the battery and not use it for about 10 years, depending on the type of battery. So don't ever say you have drained a battery! Chances are you didn't;).

Because of this, laptops use Lithium batteries, because you never fully drain them. If they were Nickel, you would have a very short battery life(Battery life as in how long it lasts, meaning how many charging cycles it can go through). Since Nickels need to be drained, and you usually don't, they never fully charge up again. The first time it might be 100%, then 98%, 95%, 92%, etc... eventually, you don't have enough volts to do anything.

As for battery calibration. You do not really calibrate your battery. What you calibrate are the sensors on the computer that read the voltage. Yes, a miscalibration will cause a misreading, and yes, 50% misreading could happen. 

Feel free to ask questions. I may now know a lot about computers, but I know my RF and electricity!:lolflag:

---

### Post by pkhetan on 2010-08-18
> **Grenage said:**
> When I've come across batteries that are so poorly calibrated, they have been beyond saving (if such things are ever possible).  Perhaps someone with more laptop experience will post here, and prove me wrong!

I may be exaggerating about the 50%, but my point is that if the battery need calibration then you have to empty it, otherwise there is no meaning of calibration. If the system read the actual power amount of a battery as 1.6% for example and decide to shutdown, then when start charging it will start from 1.6% and so on.....
In that case, what does "calibration" stand for? 

If the system doesn't shut down even it reads 0%, then each consumed Wh after that 0% will be calculated in the re-evaluation of the capacity that the system thought the battery had

---

### Post by pkhetan on 2010-08-18
Yes as pizza-is-good said, calibrating the lecture of energy amount the battery has at a certain moment.

So back to my first question :

How do i disable the "save and shutdown" forced by Ubuntu when it reads (this lecture is not necessarily true) that the battery power is critically low ?

---

### Post by pizza-is-good on 2010-08-18
> **pkhetan said:**
> if the battery need calibration then you have to empty it, otherwise there is no meaning of calibration....

Wrong, a little.

No you do not have to empty it. The biggest problem here is that laptops use software to measure the voltage of the battery. A serious design flaw. You have to use hardware to measure it. You will then get an accurate reading every time, and with that information the laptop will be able to make right decisions about what to do. There are too many variables when measuring via software, and too many ways to get it wrong. That's why there is a need to re-calibrate.

The reason you 'need' to drain the battery to calibrate is because the software says so. And, please read what I said in my previous post about draining batteries. That tells you how much the software guys know about fixing a battery. You can't drain it with your computer. That will never happen.

And a note to laptop designers: Please get accurate volt readings by using a simple voltmeter. That will not take up much space and it will save a lot of trouble on the whole battery calibration issue.
Maybe it is done that way so that users HAVE to buy replacement batteries. As an engineer myself, I think that is just sad.

---

### Post by pizza-is-good on 2010-08-18
> **pkhetan said:**
> Yes as pizza-is-good said, calibrating the lecture of energy amount the battery has at a certain moment.

So back to my first question :

How do i disable the "save and shutdown" forced by Ubuntu when it reads (this lecture is not necessarily true) that the battery power is critically low ?

OK, sorry, I shouldn't have gone off topic... At least you now know a little more about batteries.

In answer to your question, I don't know.

I really do wonder why you want to do that. It is not safe. I have done corrupted data recovery, very few things are recoverable when there is an unsafe shutdown. Let the computer safely take itself down so it can prevent data loss.
I'm not trying to be hard on you here, just helping you out.

One other thing, what did you mean when you said "this lecture is not necessarily true"? If I am wrong about something, please let me know. I'd like not to make a fool of myself in the future by stating wrong facts.

~pizza

---

### Post by Grenage on 2010-08-19
Hi, pizza-is-good.

Cheers for the in-depth post, is was pretty thorough.  I am/was aware of most of that information, with the exception that Lithion bats aren't damaged by a complete drain.  I was using the word 'calibration' merely as a way oy relating to the initial query.

That said, I thought that battery readings were performed by hardware; I thought the motherboard was rating the V!

---

### Post by anirudhtomer on 2010-08-19
by the way thanks for posting this thread. I will do a small time project solving this & making a change in that application would teach a lot to a newbie like me

---

### Post by pkhetan on 2010-08-19
> **pizza-is-good said:**
> OK, sorry, I shouldn't have gone off topic... At least you now know a little more about batteries.

In answer to your question, I don't know.

I really do wonder why you want to do that. It is not safe. I have done corrupted data recovery, very few things are recoverable when there is an unsafe shutdown. Let the computer safely take itself down so it can prevent data loss.
I'm not trying to be hard on you here, just helping you out.

One other thing, what did you mean when you said "this lecture is not necessarily true"? If I am wrong about something, please let me know. I'd like not to make a fool of myself in the future by stating wrong facts.

~pizza

No, you are welcomed for your precious informations and i have to thank you for that, so thank you very much !

"this is not necessarily true" : suppose that the OS read the remaining battery power as 1.6%; for him, this is critically low. But it's not necessarily true that this is critically low; because the real remaining battery could be more than that 1.6% as the lecture need re-calibration

For the dangerousness of waiting until the computer can't work any more and power off suddenly, it depends on what applications are open at that moment. I remember with an earlier version of Ubuntu, there was an option : "do nothing" and that didn't lead to a harmful loss of data (unless you are opening a file with OpenOffice). I used to drain batteries -once a month- slowly over the night, just leave the computer -all applications closed- and go sleep. I have never caused an unrecoverable damage to my OS.

---

### Post by pizza-is-good on 2010-08-20
> **Grenage said:**
> Hi, pizza-is-good.

Cheers for the in-depth post, is was pretty thorough.  I am/was aware of most of that information, with the exception that Lithion bats aren't damaged by a complete drain.  I was using the word 'calibration' merely as a way oy relating to the initial query.

That said, I thought that battery readings were performed by hardware; I thought the motherboard was rating the V!

I though any competent designer would have put a hardware V-meter in a laptop. Oh well. The fact that laptops get de-calibrated often is what leads me to think that it is a software measurement, not a hardware one. What I mean is the motherboard will do different things to see how the battery reacts and so forth, and that leads it to 'guess' (sometimes accurately, sometimes not) the V of the battery.

> **pkhetan said:**
> No, you are welcomed for your precious informations and i have to thank you for that, so thank you very much !

"this is not necessarily true" : suppose that the OS read the remaining battery power as 1.6%; for him, this is critically low. But it's not necessarily true that this is critically low; because the real remaining **[COLOR="Red"]usable charege of the[/COLOR]** battery could be more than that 1.6% as the lecture need re-calibration

For the dangerousness of waiting until the computer can't work any more and power off suddenly, it depends on what applications are open at that moment. I remember with an earlier version of Ubuntu, there was an option : "do nothing" and that didn't lead to a harmful loss of data (unless you are opening a file with OpenOffice). I used to drain batteries -once a month- slowly over the night, just leave the computer -all applications closed- and go sleep. I have never caused an unrecoverable damage to my OS.

While I agree with the statement I edited in your post, keep in mind that it is not 1.6% of the battery charge that is remaining. It is that there is 1.6% left of the usable charge that the laptop needs. Other than that, you are right, if it is miscalibrated, it will cause a wrong reading.

The drain it every month thing you describe might be useful for Nickel batteries. Of course, if you were doing it to recalibrate the laptop, then that is OK. I'm glad you never had data loss or corruption. If I had to do that, I would turn off the laptop, take out my HDD, and let a LiveCD drain the battery!:lolflag:

You are right that a full drainage of a Lithium might be harmful, at least practically. Not on paper, since realistically, it will never get to 0 VDC. Then again, as I said, electronics don't fully drain batteries of any kind. You'd need a 'de-charger' to get it to 0 VDC.

~pizza

PS. I apologize for misinterpreting what you meant by 'lecture'. Now I realize you meant 'reading'. I thought you were referring to my lecture, or 'class' on batteries, in the sense of a college lecture. Go figure, us Americans have really changed the language.. :(

---

### Post by bilkay on 2010-08-20
> **pizza-is-good said:**
>  ... Feel free to ask questions. I may now know a lot about computers, but I know my RF and electricity!:lolflag:
OK, so would plugging the laptop in whenever practical extend battery life? What about keeping it plugged in?

---

### Post by pizza-is-good on 2010-08-20
> **bilkay said:**
> OK, so would plugging the laptop in whenever practical extend battery life? What about keeping it plugged in?


Assuming you have a Lithium Ion battery (standard nowadays), absolutely!
Batteries are limited to 'charge/discharge' cycles, a common number would be somewhere between 300-500 full cycles of charging it and discharging it. if you always keep it plugged in, and you never use the battery, you are not using up any of the cycles. This will definitely extend battery life.

I use my laptop as my desktop as well. When at home, it is always plugged into the docking-station. This keeps my battery full all the time, so if I ever need to take the computer somewhere, it will be at full capacity.
It is good to sometimes use the battery a little bit here and there to keep it 'alive'. If it is lithuim, using it till you get to 75-80% usable charge left will not use up any of the cycles, but will rather give the battery a little extra kick here and there.

Keep it plugged in when you can, it will dramatically increase battery life-span.

---

### Post by SoFl W on 2010-08-20
What about [apcaccess]("http://www.digipedia.pl/man/doc/view/apcaccess.1/")?  I haven't used it in a while so I am not sure of the options it has.  You could disable power management and let apcaccess do whatever you want.

---

### Post by slush1000 on 2010-10-19
Hi pkhetan,

I've just started trying Ubuntu on my netbook after have been using Kubuntu for many years. So far, I am not a big fan but decided to give it a good chance :)

That was one of the configurations that I could easily do in KDE and was disappointed that there was no option in System>Preferences>Power Management to disable it.

Anyhow after much searching I found a solution...

Alt-F2 and launch gconf-editor
Navigate to apps>gnome-power-manager>actions
Change the value of critical_battery to "nothing"

After closing Gconf-editor go into System>Preferences>Power Management to confirm that it worked. It should say "Do Nothing" in that selection box now.

---

### Post by pkhetan on 2010-10-19
WOW slush1000 !

You are WONDERFUL.

You just give a direct simple easy resolution to my problem.

I'll ask you another question since you seem to be strong :
When I have more than one layout keyboard language, there will a symbol (3 letters) for the active language at the upper right panel. How could i change this symbol? When i Have the English for example, It's shown in the pannel as "USA", I want it to be "Eng" instead

Many thanks

---

### Post by Glum_Reaper on 2011-04-08
> **slush1000 said:**
> 

Anyhow after much searching I found a solution...

Alt-F2 and launch gconf-editor
Navigate to apps>gnome-power-manager>actions
Change the value of critical_battery to "nothing"


Brilliant! Thank-you very much. I've been searching for this same answer myself.

In reply to those respondents who questioned the usefulness of such a setting, I shall explain my use case (which does not seem to be unique). 

I run Ubuntu on my macbook. There is apparently a known bug with Ubuntu on macbooks becoming unable to read the battery level, which leads to the situation where as soon as I disconnect the A/C, whatever the battery charge level, the system will hibernate. Also if I start the system up on battery it will randomly hibernate when it suddenly gets to thinking there's no juice left. It definitely seems to be a software problem. MacOS will read the battery level in agreement with the leds on the battery itself. I can be 'hibernated' out of Ubuntu and then reboot into MacOS and find it shows 80% battery charge.

Add to this the fact that I often use my laptop on my lunch break, an hour. The battery works fine for several hours so there's usually no need for me to have it plugged in at lunchtimes. However, I've been finding that I spend up to twenty of my sixty minutes waiting for the system to hibernate then reboot when I suddenly get warned about the 'critical battery level'.

So in this case, there really is no danger of damaging the system - the battery isn't going to run out in an hour (and I can always use the charge level LEDs on the battery itself if I want to be sure it's got enough). But being able to avoid the frequent without-warning, enforced hiberations is very handy!

My suggestion for improvement would be to make the 'cancel' button on the 'laptop battery is critically low' dialogue actually cancel the hibernation. I can't imagine why there are 'ok' and 'cancel' options when they both lead to the same thing.

Thanks everyone!

---

### Post by yaywoop on 2011-05-10
@pizza-is-good just to pick you up on a few things..

1. discharging the battery to zero volts is actually impossible in a Lithium laptop battery because the battery pack has circuitry built in which monitors voltage and charge (this is all done in the battery, not on the motherboard) the circuitry will kill all power to the laptop when any of the cells get below about 2.8V or 3V. Thus it is safe for the battery to be "fully discharged" as it will never go outside of the safe range unless the circuitry fails. This safety mechanism is totally independent of software/OS or even the motherboard and BIOS..

2. When we talk about percentage of actual battery energy we are referring to the useful percentage, this is the power available within the save voltage range of the cells (3.0 to 4.2V per cell) 
and the actual percentage is not always reported by the operating system correctly, this is probably a fault in the calibration of the electronics built into the cell, not the laptop.

3. Modern filesystems (EXT3/4) will rarely become corrupt if power is suddenly removed as they use journaling. and if corruption does occur it will only be in the files being written to at the time power was removed.

reference en.wikipedia.org entries for Lithium-ion_battery and Journaled_filesystem

Anyway back on topic, thanks slush100 thats exactly what I needed.
Was running ubuntu 10.10 on my eeepc1000h, getting about an hour of battery life before it would suspend. One day I changed the critical battery action to hibernate, which failed, so ubuntu removed the option of hibernate and set the critical battery option blank. Suddenly I was getting an extra hour or so out of by battery! So when it reported 0% the battery was actually at about 50%.
After this extra hour the protection circuitry would kick in and it would loose power. Never ever had corruption, and I did this daily :D

Now Im running 11.04 and they fixed the hibernate issues so I came searching for that solution.

---

