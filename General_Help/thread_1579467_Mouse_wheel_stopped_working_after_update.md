---
title: "Mouse wheel stopped working after update"
date: 2010-09-21
forum: General Help
---

### Post by Replicon on 2010-09-21
Hi all,

Stupid situation, with probably a really easy fix: My mouse wheel stopped working after a package manager update.

I'm still running 8.04 (yeah, yeah, I know, will be updating soon). I can't seem to find a "package manager update history" so I can see what got updated when I did that just today (changes can't be more than 24h old).

I tried rebooting/cold boot just in case.

I check xorg.cfg, but it hasn't changed since march of 2008, so I figure nothing overrode the config.

Help? :)

---

### Post by Replicon on 2010-09-21
Oh wait duh, here's what I downloaded today:

```

Commit Log for Tue Sep 21 18:50:58 2010


Upgraded the following packages:
bzip2 (1.0.4-2ubuntu4) to 1.0.4-2ubuntu4.1
dpkg (1.14.16.6ubuntu4.1) to 1.14.16.6ubuntu4.2
dpkg-dev (1.14.16.6ubuntu4.1) to 1.14.16.6ubuntu4.2
libapache2-mod-php5 (5.2.4-2ubuntu5.10) to 5.2.4-2ubuntu5.12
libbz2-1.0 (1.0.4-2ubuntu4) to 1.0.4-2ubuntu4.1
php5 (5.2.4-2ubuntu5.10) to 5.2.4-2ubuntu5.12
php5-cli (5.2.4-2ubuntu5.10) to 5.2.4-2ubuntu5.12
php5-common (5.2.4-2ubuntu5.10) to 5.2.4-2ubuntu5.12

```

bzip, dpkg, apache, php... wtf, that has NOTHING to do with mouse wheel!!!

---

### Post by Replicon on 2010-09-22
FWIW the mouse section of xorg.cfg looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

---

### Post by sydbat on 2010-09-22
Maybe your mouse wheel just stopped working - as in a hardware problem with the mouse.

Do you have other mice you can test with to eliminate a hardware problem?

---

### Post by dolson on 2010-10-01
Edit: nevermind, figured it out... My wheel stopped working RIGHT after an update and reboot. Totally coincidence, as stated earlier in the thread - I opened the trackball and cleaned out any dirt and dust and hair I found in there, particularly around the wheel, and now it works fine once again.

---

### Post by Replicon on 2010-10-13
> **dolson said:**
> Edit: nevermind, figured it out... My wheel stopped working RIGHT after an update and reboot. Totally coincidence, as stated earlier in the thread - I opened the trackball and cleaned out any dirt and dust and hair I found in there, particularly around the wheel, and now it works fine once again.

Oh yeah totally forgot about this thread.

Same kind of total coincidence for me. I brought home a mouse from work to test with, and it's fine (and the other mouse doesn't work on the other laptop either).

cheers

---

