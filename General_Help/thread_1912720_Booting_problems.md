---
title: "Booting problems"
date: 2012-01-21
forum: General Help
---

### Post by chrislang on 2012-01-21
I have a two year old Acer M1800 Desktop running lubuntu which will not boot after returning from 4 weeks holiday. I've replaced the CMOS battery (I sometimes get a "CMOS checksum bad" error message), but this didn't help.

The computer did boot twice, but both times it froze after a couple of hours. Since then, it won't boot - it just gives a black screen with a blinking cursor. It doesn't get as far as the "grub loading" message.

I've looked through the BIOS settings, but I'm not really sure what I'm looking for. The date is set at Sat 01/01/2009. Sometimes the computer freezes while I'm looking at the BIOS settings. 

I've tried booting from a USB stick, but that doesn't work either.

Anyone got any suggestions? Thanks!

---

### Post by SteveDee on 2012-01-21
> **chrislang said:**
> ...I've tried booting from a USB stick, but that doesn't work either....

It does sound like a hardware failure.

I've had old Acer laptops (TravelMate 290 series I think) that will not boot from a LiveCD, and have been surprised to find that they will boot from a CD if I remove the hard disk drive (eventually replacing the HDD fixed the problem).

So I suggest you try that.

---

### Post by imachavel on 2012-01-21
well you can replace the hdd all you want, but if you change the cmos battery, then that might have changed something. What we need is more detail, what happened that made you change the cmos battery? Did the problem with boot start before or after you changed the cmos battery?? 

I can't understand what the hdd would have to do with anything, unless you had OS, bsod, or what not for sure definite hdd problems before this booting problem you have currently. Please tell us why you changed the cmos battery, don't forget hdd is the last thing that boots, the bios loads, then detects the interface the hdd is connected to, that is IF the bios is reading this as selected boot device.

---

### Post by 2F4U on 2012-01-21
I would start by setting the date to the current date and also the time. Linux, as most other operating systems don't like it if the current date is in the past. I guess that you changed the CMOS battery since the old one was dead. If that is true, you've probably lost all previous BIOS settings. Did you load default BIOS settings after changing the CMOS battery? Else you may have some wierd BIOS settings.

---

### Post by chrislang on 2012-01-22
Thanks for the replies. @imachavel - sorry, I can see why you need more details... The problem started before I changed the CMOS battery. Here's what happened in chronological order:

1. I came back from four weeks holiday and the computer would not boot.

2. The next day it did boot, but froze after a couple of hours. I pulled out the plug, waited a minute, put it back in and the computer started up, but froze again after an hour or so.

3. I kept trying to boot. Usually what happens is that instead of the message about "grub loading", I get a black screen with a blinking cursor. Sometimes though I get a "CMOS checksum bad" error message. This made me think it might be the CMOS battery that's the problem. That's why I changed the battery.

@2F4U - I loaded default bios settings. I've now changed the date. I'm still not getting past the black screen with the blinking cursor.

---

### Post by varunendra on 2012-01-22
> **imachavel said:**
> I can't understand what the hdd would have to do with anything
A failing hard disk or a bad connector can do amazing things to your computer :)

My preferred way to troubleshoot such issues [COLOR=Red](**only the emboldened parts seem relevant** to me for OP's problem, but I'm mentioning my full general routine)[/COLOR]:

[LIST=1]
[*][COLOR=DarkRed]**Detach everything from the motherboard, except the CPU.**[/COLOR]
[*][COLOR=DarkRed]**Clean the system and all the parts with a brush or pressure blower.**[/COLOR]
[*]Clean the contact pins of the RAM with a rubber eraser
[*][COLOR=DarkRed]**Re-connect only the motherboard and CPU power cables, power switch, keyboard/mouse/monitor, and re-seat RAM. (No drives or add-on cards connected yet)**[/COLOR]
[*]Power on the CPU > get into BIOS > check Voltages and temperatures for a while.
[*][COLOR=DarkRed]**Connect only a bootable USB flash drive (if you are sure the system is able to boot from it, confirm in the BIOS) > restart > try to boot from it.**[/COLOR]
[*][COLOR=DarkRed]**If USB booting fails, connect the optical drive and retry with a bootable CD (with USB drive removed).**[/COLOR]
[*][COLOR=DarkRed]**Reconnect hard disk and retry to boot**[/COLOR]
[*]Reconnect other addons/cables
[/LIST]
**_Failures and conclusions_:**

[LIST]
[*]If system hangs/fails to boot at **step 5**, either PSU or the motherboard itself is defective, or the CPU/CPU-heatsink needs to be re-seated. Possible problems and solutions are many, ranging from just re-seating CPU to taking the mobo to a repair shop :P
[*]If it hangs on **step 6 or 7**, RAM is the prime suspect. Although there maybe driver/motherboard issues as well.
[*]If the failure occurs with **step 8** only, hard drive is failing and needs to be replaced.
[*]If the failure occurs after **step 9**, some cable or addon card is either defective or the card has problems with BIOS settings or drivers.
[/LIST]


**_PS_:**
If I have to rely on guess, I'd remove the hard disk and try to boot with a live cd/usb. If it still fails, I'd go through above routine.

---

### Post by SteveDee on 2012-01-22
> **varunendra said:**
> A failing hard disk or a bad connector can do amazing things to your computer...
I'm glad someone agrees with me. We take HDD for granted, but they can last for years or fail within 15 months.
They sit on a bus and if their circuitry fails, its anyone's guess how this may affect the m/brd or any running code.

I didn't mean to suggest that chrislang should replace his HDD, only that it should be removed to see if the laptop boots from a LiveCD/USB.

> 
My preferred way to troubleshoot such issues...

 
I agree with most of what you say with 2 exceptions, and 1 comment.

 - I no longer advocate cleaning the inside of computers except where dust & dead spiders are blocking airways (e.g. cpu heatsinks & fans). Household dust is not conductive, so not a problem. Static electricity is a problem, so don't just clean for the sake of it!

 - I use to use pencil rubbers/erasers on the gold plated contacts of plug-in cards. But that was when the circuitry was analogue, not digital. Again, the risk of generating several kV across the pins of a memory chip is not worth taking. If you run a memory test and see errors, then you can carefully remove your memory (preferably while wearing an anti-static wrist-band), blow any dust out of the slots, then replace them and try again.

...and my comment, you can break down most desktop computers fairly easily (like Lego). But laptops are very difficult to dismantle, apart from the HDD and the RAM. So don't attempt it on a valuable machine unless you are very experienced.

---

### Post by varunendra on 2012-01-22
> **SteveDee said:**
> Household dust is not conductive..
True, but if a system is old enough to have accumulated a lot of it on the board and then is left unused for a while, there is always a chance of it _catching moisture_ which may then cause startup problems when the computer is switched on again.

Actually I got this experience first (many times), and knowledge of 'why it happens' later. Having worked as an amateur hardware professional a few years ago, we used to get a lot of old systems with tons of dust settled on the board and everywhere. After a while, with repeating experiences, it became our routine exercise with old and dirty boards to first wash them with diluted thinner to clean the sticky dust, then dry it with hot blower. In more than 60% cases, it was all we had to do to fix POST issues!


> **SteveDee said:**
> But that was when the circuitry was analogue, not digital.... Analogue? Sorry I didn't get it. I would like to know more about this point if you don't mind sharing.:) Although the 'cleaning with eraser' part is definitely something to be done carefully, and only if seems necessary (based on visual appearance of the contact pins).


> **SteveDee said:**
> ...and my comment, you can break down most desktop computers fairly easily (like Lego). But laptops are very difficult to dismantle, apart from the HDD and the RAM. So don't attempt it on a valuable machine unless you are very experienced.
Yeah, that's totally correct and advisable. Although you should have mentioned that this comment of yours is a general one, not specifically targeted to the OP, since his system is a desktop, not a lappy-
> **chrislang said:**
> I have a two year old Acer M1800 Desktop....

Well.. let's wait for the OP to see if he managed to make any progress.

---

### Post by SteveDee on 2012-01-23
> **varunendra said:**
> ...as an amateur hardware professional...

Hmm, does that mean you were a volunteer?

> 
...old systems with tons of dust...

sounds a bit extreme...

> 
Analogue? Sorry I didn't get it. I would like to know more about this point if you don't mind sharing.

My working career (mostly in industry) goes back a long time. I was a hardware engineer in the 1970s & early 80s, designing and working on analogue computers and digital systems (including 6502, 8085/86/88 ). Plug-in cards with non-static sensitive circuitry can be cleaned with an erasor. I'd guess that the majority of readers on this forum are not professionals...so my recommendation here is "don't do it!"

> 
I have a two year old Acer M1800 Desktop....

Ha-ha! You've got me there. I was working on 2 or 3 replies at the same time...now, who was the guy with the laptop I thought had a desktop?

---

### Post by varunendra on 2012-01-23
> **SteveDee said:**
> Hmm, does that mean you were a volunteer?
..kind of .. yeah. It was a repair shop of one of my brothers' friends. I joined it in hope of getting some knowledge and experience. But soon found out that most of those people in the market know next to 'nothing', and earn their living by tricking people.. So I figured it was not my thing.. ;)


> **SteveDee said:**
> sounds a bit extreme... obviously it is (tons!!.. well multiply it with a few negative powers of 10..):D
But systems with too much 'sticky' dust on the boards can be commonly seen on these repair-shops. If you see one of them, you may wonder how it was booting before coming to you..!


> **SteveDee said:**
> My working career (mostly in industry) goes back a long time. I was a hardware engineer in the 1970s & early 80s, designing and working on analogue computers and digital systems (including 6502, 8085/86/88 ). Plug-in cards with non-static sensitive circuitry can be cleaned with an erasor. I'd guess that the majority of readers on this forum are not professionals...so my recommendation here is "don't do it!" Nice to meet you sir! I'd take that advice of not suggesting others to use erasers on these modules (but I personally would still do.. :P)


> **SteveDee said:**
> now, who was the guy with the laptop I thought had a desktop?
:lolflag:

---

### Post by chrislang on 2012-01-24
Thanks for the help so far. I just tried booting from a usb stick after taking the hard drive out. It didn't work. 

I can't even get into the BIOS settings now - when I press the "Del" key, it says "Please wait" and then freezes.

It's really not looking too good, is it? Although looking on the bright side, the hard disk is probably OK...

---

### Post by varunendra on 2012-01-24
So the problem is increasing in "slow motion"! Did that happen even with all other drives/addon cards disconnected?

In this case (the gradual increment in problem's frequency and intensity), my usual suspects are:

[LIST=1]
[*]PWM section on the motherboard
[*]Failing PSU
[*]Failing RAM
[/LIST]
**Possible ways to verify/solve:**

[LIST=1]
[*]Follow steps 1 > 2 > 4 > 5 in my first post.
[*]Check whether the voltages and temperatures are normal, and how long (and how many times) you can play around in the BIOS without anything else connected.
[/LIST]
If you can't get into step 5 (get into BIOS) even without any drive,  cables or additional card connected (assuming you are using onboard  graphics), then-

[LIST]
[*]replace the RAM if you have a spare one available. And/Or-
[/LIST]

[LIST]
[*]Changing PSU would be another blind shot if the system doesn't complete POST (Power On Self Test- the 'beep' sound you hear just after powering on the system).
[/LIST]
If you don't have a spare RAM (tested ok), or the same RAM happens to work fine on any other system, and changing PSU also doesn't work, then I'm afraid its time to see a repair shop.

---

### Post by chrislang on 2012-06-19
Thanks everyone for the help and sorry about the delay. The problem was the RAM connection, which was solved by taking the RAM out and putting it into the next slot (which was conveniently free). Problem solved.

---

