---
title: "List of grievances I need fixed to fully commit to ubuntu [If you can help, please!!]"
date: 2011-04-05
forum: General Help
---

### Post by megavoltaic on 2011-04-05
So I'm really starting to get turned off of windows 7 and more to the ever expanding ubuntu (10.10). However, there's a couple things that aren't really bad, but would like fixed. Then, and only then, can I uninstall windows 7 fully from my drive. Here's the list.

[LIST=1]
[*][Solved] My battery icon does not show percent left (Except when I plug/unplug). It just shows "estimating..."
[*][Solved] My internet (wifi and eth) may not work on a boot of ubuntu. I have to retart the computer to connect to anything
[*]My wifi light keeps blinking!
[/LIST]

New List:
[LIST=1]
[*]Why does ubuntu on boot say "Cannot reserve MMIO Region?
[*]Why does ubuntu in some rare cases almost lock up (My mouse moves really slow...)
[*]Just a shot into the dark, any hope of getting PSO (Phantasy Star Online) Schthack to work?
[/LIST]

That's it for now, I'll add as I need to. Also, here's my specs

Compaq Presario CQ62
Ubuntu 10.10
64-Bit, people!!!

Links and terminal commands are great, but scripts and .deb packages are even better! :D

Edit 1:
If you need any specs, just ask!

---

### Post by coffeecat on 2011-04-05
1 - Sorry, don't know about that.

2 - Are you sure it's ethernet as well as wireless? There's an issue with the firmware with some wireless chipsets where if you do a warm reboot from one OS to another, the firmware can be left in an inconsistent state. This can affect Windows as well as Linux. The firmware needs to be loaded afresh into the device when booting occurs. If this is what is happening for you, a cold boot into Ubuntu rather than a warm boot will help. I.e, close down Windows and allow the machine to switch off, wait a few seconds and then boot into Ubuntu. See if this helps.

3 - It's meant to! :) It's showing traffic. If your wifi light is not blinking in Windows then there's something wrong with your Windows driver. Or Compaq have done something funny. :wink:

---

### Post by mr.farenheit on 2011-04-05
i agree with coffeecat on 2 and 3. for prob #1, allow your battery to charge for awhile then let it run for awhile with the a/c disconnected. also, try clicking on the power icon and go into preferences, from there you can choose how and when the power icon will show up and what to do. hope that helps.

---

### Post by Quintilian on 2011-04-05
I believe for #1, the more you use Ubuntu the more accurate the percentage will be. So if you run it off of the battery for a while it should be able to estimate the time remaining for you.

---

### Post by megavoltaic on 2011-04-05
Thank you guys for your responses!

Ok, for #1, I found out that this happens to a lot of people, and there is a fix for it. I just need to find it in 64 bit.

#3 its atually the exact same problem

#2 I've tried what you said, coffeecat, but the problem persists. Something I've noticed though: It happens every OTHER boot.

---

### Post by megavoltaic on 2011-04-05
OK, so after some intense googling, I found some answers.

To the battery icon, turns out that its a problem with the native battery manager and HP/Compaq computers, so I switched managers.

Link: [http://www.webupd8.org/2010/11/battery-status-ppa-finally-updated-with.html](http://www.webupd8.org/2010/11/battery-status-ppa-finally-updated-with.html)

And, though I havent tested it yet but I'm sure it must work, the wireless not working I fixed using ndiswrapper and some blacklisting commands

Link: [http://ubuntuforums.org/showthread.php?t=291297](http://ubuntuforums.org/showthread.php?t=291297)

I hope that helps some people who have the same problems. I'll strikethough the list now.

---

### Post by Old *ix Geek on 2011-04-05
> **coffeecat said:**
> 3 - It's meant to! :) It's showing traffic. If your wifi light is not blinking in Windows then there's something wrong with your Windows driver. Or Compaq have done something funny. :wink:My wireless light [on my HP laptop] has never blinked--nor would I want it to. (After brain surgery, I've had issues with flashing lights, dizziness, headaches and the possibility of seizures. So, yeah, not something I'd want!) It's solid blue when wireless is enabled and solid orange when it isn't. That works for me. :)

---

