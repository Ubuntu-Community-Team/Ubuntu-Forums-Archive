---
title: "Linux won't install after computer repair"
date: 2010-07-30
forum: General Help
---

### Post by Donzieja on 2010-07-30
I got my laptop repaired (by the manufacturer). Linux would install fine before, but not now, as all I get is a black screen with a blinking cursor. Note, I've only tried KDE versions of software since my laptop came back, so I don't know if that's the problem. I tried linux mint 9 and kubuntu 10.04. And all I get after a while is described above. I also tried some different install options, because I'm able to get to the menu to choose which type of install I want, but the other options led to the same thing, and it would sometimes display a bunch of numbers and then "EH ok" or something. the numbers on the left keep increasing, and eventually I get to the splash screen, where it freezes, and repeats the process. any ideas?

Thanks,

-Don

---

### Post by Strongman332 on 2010-07-30
how long does it do it. becuase its a common bug for the computer to do this 10-30 seconds, then go to log on screen. try letting it sit for a minuet

if that does not work send it back and have them fix it

---

### Post by Donzieja on 2010-07-30
It does it for... i turned it off after 10 minutes

---

### Post by Donzieja on 2010-07-31
Okay, so i got it to install after about 2 hours, then it takes about 30 minutes to boot. this has been happening in all variations of linux that I've tried.  any ideas?

---

### Post by jerenept on 2010-07-31
> **Donzieja said:**
> Okay, so i got it to install after about 2 hours, then it takes about 30 minutes to boot. this has been happening in all variations of linux that I've tried.  any ideas?

:shock:

run ```
dmesg tail
``` in a terminal and give us the results here. Does the computer operate normally after you install? the problem may be corrupted or scratched cd's (or dvd's).

---

### Post by Donzieja on 2010-07-31
It runs fine after all the booting and installation.

---

### Post by Donzieja on 2010-07-31
I'm reinstalling linux mint 9 kde now. So it's gonna be a while before I get back with that information.

---

### Post by Meow27 on 2010-07-31
could be that the repair resulted in replacement of hardware (like upgrades, new hardware etc). 

and new hardware is not likely to have linux drivers. problem shouldn't persist in the next one or two ubuntu releases.

edit--
and could you state what modeltype your machine is?

---

### Post by Donzieja on 2010-08-01
Gateway NV52

---

### Post by Donzieja on 2010-08-01
Yea so linux mint froze at a bunch of different points... I should also add that it works lightning fast in virtualbox under windows.

---

### Post by Donzieja on 2010-08-01
Can anyone think of anything?

---

### Post by DarthScape on 2010-08-01
I would try booting to a minimalistic distro, like puppy linux or something to see if that even loads. Maybe try installing linux to a flash drive and start from there, what what that does for you.

---

### Post by Donzieja on 2010-08-15
Alright. None of that works.

---

### Post by Karl1982 on 2010-08-15
What was the repair on the machine?  Is it possible your defective/damaged part(s) were replaced with defective parts that exhibit different symptoms?

Also, you need to verify your installation media.  Boot to your CD and have it check for defects.  You might also try grabbing unetbootin and installing from USB, see if it does the same thing.  My experience (with Ubuntu and many other things) has been freezing up during boot or installation is more often than not a bad disc or bad drive.

---

