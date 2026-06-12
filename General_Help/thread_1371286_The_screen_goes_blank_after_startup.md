---
title: "The screen goes blank after startup"
date: 2010-01-03
forum: General Help
---

### Post by Key-Tech on 2010-01-03
Hi All,

I've recently installed the 64bit version of WUBI on ASUS K50IJ with windows 7. Everything went smooth however when I try to boot into ubuntu, it shows that all the drivers are loading, I can even see the desktop background image for a second and then the screen goes blank. It is still ON however nothing is showing on it.
Pressing "CTRL+ALT+DEL" reboot the system.

Do you have any idea how to solve the problem, or even get access to the console for further debugging?

---

### Post by Key-Tech on 2010-01-03
OK, I've tried to use the Live CD to boot into Ubuntu but it also failed. I saw the Live CD menu but even when I used the safe graphic mode it still didn't boot into ubuntu, I can't even see the progress bar.:confused:

---

### Post by MooPi on 2010-01-03
If your install is brand new you won't be loosing anything by attempting to re-install with the live CD. That is if your able to boot and use the live CD?

---

### Post by Key-Tech on 2010-01-03
Thanks for the replay.
At first I tried to just run the live CD to try and see if ubuntu support the hardware, since I could not reach the desktop using the Live CD option, I've tried installing wubi. but again after the grub menu i can't reach ubuntu desktop (I can't even see the progress bar).
I suspect the intel video driver but i have no idea how to bypass it.

---

### Post by MooPi on 2010-01-03
If the live CD didn't work, it's probably a good guess that a full install maybe fruitless. Can you list the spec's for your computer?

---

### Post by Key-Tech on 2010-01-03
I have an asus K50IJ notebook with intel GMA4500M

---

### Post by MooPi on 2010-01-03
It would seem that your laptop should be able to handle Ubuntu just fine. I did a quick search and not much came up for your graphics chip. Just anecdotal evidence it may have buggy graphics.

---

### Post by Key-Tech on 2010-01-03
Thanks a lot for your help MooPi.
Do you know a way for me to by pass the video driver an boot directly into the console?
I've tried to look for some way to do this with some grub options but couldn't find it.

---

### Post by MooPi on 2010-01-03
When you get to the grub post select recovery console. This is a command line version of Ubuntu. At the moment I'm not certain what you can do from there. I'm going to look into it as I suggest you do as well.

---

### Post by Antlong on 2010-01-03
Hello all,

 I should like to add my plaintive voice here, if I may!

  On this Lenovo netbook: I was playing with Firefox, came across a security.ubuntu.com problem, established in general terms what it was referring to and that it might be easier just to reinstall Ubuntu and 
upgrade to 9.04.

  Succesfully installed, it said, please to do a restart. But the screen is blank. Now, there is always a totally dark screen whether booting off the hard drive (it starts running and clicking, then stops clicking; stays
running 'til I switch off again) or via the external CD drive (which lights up, flashing, for a few moments while clicking, then runs down).

  I've tried the Ubuntu CD which originally installed ok, and also the one  from which I'd first installed Ubuntu instead of XP.

  I wondered if I'd inadvertently switched off the screen, but apparently 
not - in any case, presumably it would default to On? I've also looked for 
something on an external screen, I know that works because I played with 
it a few weeks ago. fn-F" to toggle the screen doesn't do anything, nor fn-up/down to change brightness. I'vce just tried ctrl-alt-backspace, with CD and HDD, to no effect.

  The battery's fully charged but in any case I'm using the psu and all 
lights are correctly lit. I've reseated the CD leads several times to be 
sure.

  I've never networked it to the desktop - it had seemed a good idea to keep them separate so only one gets broken...

  Apart from all that, Happy New Year to all!

Regards Ant

---

### Post by MooPi on 2010-01-03
Try this command when you enter recovery.
```
sudo dpkg-reconfigure xserver-xorg
```
 reboot

---

### Post by Key-Tech on 2010-01-04
Unfortunately I can't even go into the recovery mode. I see all the drivers that are loaded and I see the background image for a second and then the screen goes blank again. The screen is ON (I can see the back light) but nothing appears on it. 
I will try to remove wubi and re-install it. I'll update on the results later on.

---

### Post by Key-Tech on 2010-01-04
OK, after doing some more searching on Intel GMA 4500M problems ,I've found the following thread:
[http://ubuntuforums.org/showthread.php?t=1311148&referrerid=214733](http://ubuntuforums.org/showthread.php?t=1311148&referrerid=214733)

In it they suggested to add "i915.modeset=0" to the grub options and it solved my problem :guitar:

So again, thank you Moopi for your help

---

