---
title: "gigabyte ga-ma785gmt-ud2h crashes often?"
date: 2009-11-03
forum: General Help
---

### Post by wotsit on 2009-11-03
multiple problems here... just wondering what peoples thoughts are... tried multiple different installs of 9.10 9.04 8.04 without much luck, tried the proprietary and open source drivers

the crash happens at 2 different times. either after the boot menu, or when you're on firefox or eclipse, or when you have a few applications running at the same time.

the crash after the boot menu has lots of **É****É****É****É****É****É****É    ****É****É  ****É****É****É****É **characters dancing across the screen refreshing about every quarter of a second, with other random characters dotted in. you cannot do anything apart from switching the thing off and on and trying again.


the crash when youre using the system is either just a reboot straight away, or a freeze, with narrow blue bars about an inch long clustered in groups in about 5 columns.

driver problem? or hardware? interference from something? sometimes, the system is useable for long periods of time, sometimes you have to try 2 or 3 times to log in. ive never had a crash whilst watching videos, for some reason.

i am using 9.10 with
500gb wd hdd
amd phenomII 550 black ed
ati radeon hd4200


should i try a graphics card to see if it is the hd4200 onboard graphics causing the problem? i dont happen to have a card however... anything you guys want me to type in the terminal?

---

### Post by Giblet5 on 2009-11-03
I would suspect hardware first. It's the easiest to diagnose anyway.

Run the "memtest86" test from the boot menu.

It should be able to run continuously for four hours with no errors.

Do you have Windows installed and bootable? If so, install Prime95 and run the default test. That will test all cores running at 100% load and spot timing or thermal issues.

If you can do BOTH of those successfully your hardware is much less likely to be a suspect, although an overheating graphics card can do some weird stuff.

---

### Post by wotsit on 2009-11-03
no, i dont have windows installed. ill run the test overnight and see what happens, i hope it isnt hardware. 

[http://ubuntuforums.org/showthread.php?p=7713897](http://ubuntuforums.org/showthread.php?p=7713897)

the above thread gives me hope as there seems to be a few issues with bios settings for the hdd settings, clock frequencies, and others.

i think i'll play around with a few things in the bios and see what that does.

wish i knew what it was !

EDIT

yeah the onboard graphics ive heard can get overheated on this board. but its not like im doing anything stressful. and the fact that it never crashes when running movies fullscreen makes me think it could be a bios thing. maybe.

---

### Post by P4man on 2009-11-03
Definitely sounds like a hardware issue.

---

### Post by Giblet5 on 2009-11-03
> **wotsit said:**
> no, i dont have windows installed. ill run the test overnight and see what happens, i hope it isnt hardware. 

[http://ubuntuforums.org/showthread.php?p=7713897](http://ubuntuforums.org/showthread.php?p=7713897)

the above thread gives me hope as there seems to be a few issues with bios settings for the hdd settings, clock frequencies, and others.

i think i'll play around with a few things in the bios and see what that does.

wish i knew what it was !

EDIT

yeah the onboard graphics ive heard can get overheated on this board. but its not like im doing anything stressful. and the fact that it never crashes when running movies fullscreen makes me think it could be a bios thing. maybe.


It's those BIOS timing settings that can cause trouble like this.

This box runs an Asus mobo with a Q6600 quadcore cpu. That cpu is rated at 2.44Ghz. I'm running it at 3.40Ghz, almost 30% over what it's rated for.

That's handy, but it took HOURS of tweaking and testing to make this box stable at those high frequencies.

memtest86 and prime95: if you can run them both for four hours w/o a hiccup, your basic hardware is pretty much beyond reproach.

If you can't run windows *native*, memtest86 alone is a good test of memory timing. So do that. I'm guessing that you'll get intermittent errors. That's either timing or power supply.

Corsair memory sticks are rated with an assumption that you will pump non-standard voltages into them via BIOS settings. You can have problems if you don't tweak the RAM voltage.

Check your memory vendor's recommendations for the model of RAM sticks you have. Make sure it's set to what they recommend, Then test with memtest.

---

### Post by wotsit on 2009-11-04
I haven't installed flgrx or whatever-it-is-called driver, no compiz, and i haven't installed flash. No crashes in 24 hours, compared with crashes every two hours previously. Still have intermittent problems with grub not loading, or grub menu failing to load the os. Maybe it is the graphics card which is playing up. Or drivers for the card being buggy for the 4200. Will keep you posted...

---

### Post by P4man on 2009-11-05
that corruption you see in grub points to a serious problem with the videocard and/or bios.sounds like something is overheating? Did you try updating your bios? Either way this is not a linux problem but a hardware one for sure.

---

### Post by wotsit on 2009-11-07
OK, I've done memtest and it ran for 4 hours when i was at work for a half day. Test completed, no errors, press esc to reboot. There is nothing wrong on that side of things whatsoever.

The crashes now are a lot less frequent. I had one this morning, on first turning on the computer. I now do not get any crashes except just before the boot menu, and usually first thing in the morning.

After a reboot, occasionally two, i never get a crash. That has been for 3 days now. I am positive it had something to do with flash or a dodgy custom theme.

So my question: I am still sceptical that the crashes are hardware related. Is there any utility similar to Prime95 for Linux which I can use to test other hardware such as the graphics?

---

### Post by P4man on 2009-11-07
to stress test the cpu, perhaps install BOINC from the repo's.
For the videocard, a 3D game would do I imagine.

---

### Post by jejones3141 on 2009-11-26
I don't see crashes, just failure to boot--has to be a hardware or BIOS issue, because the hang is long before Ubuntu gets control. To boot, I have to disconnect the SATA hard drive, boot, then power down and reconnect the SATA drive.

When it runs, it runs beautifully.

---

### Post by wotsit on 2009-12-09
turns out it was the onboard gpu... I rma'd it and its being delivered in a few hours. Spot on with your diagnoses, guys, well done, and thanks.

---

