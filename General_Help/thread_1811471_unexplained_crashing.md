---
title: "unexplained crashing?"
date: 2011-07-24
forum: General Help
---

### Post by mrule on 2011-07-24
-- seems to be related to web browsing
-- chrome or firefox, doesn't matter,
-- even trying to use this forum crashes the machine

when it crashes :
-- screen freezes, mouse freezes, keyboard does nothing
-- sometimes goes to black screen and then either
-- -- reboots
-- -- logs off and returns to login screen

if it persists in 'screen frozen' stage, 
-- remote login is possible
-- the remote login is the only user, the user for the gdm session or whatever is missing / kicked off
-- nothing especially bad is happening in top or the list of processes
-- -- although sometimes xorg will be running at 100% cpu

how do I go about debugging this ? i am out of ideas.

---

### Post by mrule on 2011-07-24
and.... crashes are no longer happening ? what could have happened ?

---

### Post by 2F4U on 2011-07-25
Did you check the log files after the crashes happened? Did you install updates? A fix for the crashes may have been provided with the updates. With that little information you provide its almost impossible to guess.

---

### Post by mrule on 2011-07-25
I was asking, which log files should i check, how do I check them, and what do I check them for?

The machine is up to date on updates, but the crashes continue as previously described.

I need help knowing what information to find and where to find it, in order to start figuring this out.

---

### Post by bovender on 2011-07-25
I've been experiencing mysterious crashes for a while now as well. Had one just now, and this prompted me to search the forum.

I also think it's related to browsing. I use Opera and Chromium, and most crashes happen when Chromium is running. However, when it crashed just now, I had Opera (and Claws Mail) running.

The screen flickers, and then everything freezes. I have to press the Power button 4 seconds on my laptop to shut it off.

Sometimes, when I'm quick enough, I can kill the X server (CTRL-ALT-DEL) as soon as the flickering starts.

It appears that there is some kind of graphics problem. Maybe with the font rendering of the newer browsers???



In any case, Ubuntu has now clearly surpassed my old Windows machine in terms of frequent crashes :(

---

### Post by dino99 on 2011-07-25
crashes can happens for many reasons:

- hardware: are your fans running well ?
- is your hardware not too dusty ? can it catch some fresh air ?
- ram stick issue (use testdisk or valgrind)
- is swap used ? is it large enough ?
- psu quick dropdown
- ....

- software buggy (watch logs, eg /var/log/, to find usefull errors)

---

### Post by mrule on 2011-07-25
something else I will note is that the crashes do not happen when I boot into 'recovery mode' and use a low-graphics session.

recovery mode may turn off other things besides graphics, so this doesn't mean its graphics per se.

I'm using an nvidia graphics card with their provided drivers. My best guess is that there are bugs in the nvidia drivers, which are causing the crashes. It is possible that web browser rendering stress tests the graphics drivers and tends to bring about crashes more quickly.

However, I am slightly confused by the fact that the crashes happen in both chrome and firefox. Do these browser share common code at some level, or do something similar that might invite crashes ?

Checking for hardware failures sounds like a good idea, I can open up and clean out the case.

However, the fact that low graphics mode mostly resolves the issue is suspicious. Perhaps only the graphics card is bad, or perhaps this really is a software bug somewhere else.

---

### Post by mrule on 2011-07-26
Ok, I've had similar problems with graphics before. The NVIDIA drivers may be buggy, or at least the bug related to them. It is also possible that there is a hardware problem with the card, but I would hope that the drivers would be able to detect such a problem rather than crash the entire system.

---

