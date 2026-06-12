---
title: "A Glitch with Firefox"
date: 2011-05-29
forum: General Help
---

### Post by Bigneil on 2011-05-29
I don't know if this is the right subforum for this, but here goes.

I am currently running 11.04 on my laptop. Firefox is struggling to cope with images for some reason. Whenever there are pictures on screen in firefox the computer slows down to a glacial pace.

I tried clearing out the history and cookie files, and i have tried uninstalling and reinstalling FF but the problem still persists.

I have tried other browsers that worked fine with images, but didn't find any that i really liked.

If any of you guys have suggestions on how i can sort it out I'd love to hear them.

---

### Post by blueridgedog on 2011-05-29
When running firefox, do you have free resources or is the system struggling?  Run firefox and reproduce the issue then run the following command in a terminal:

```
free
```

That well show the amount of free memory you have.  

Also:

```
df
```

This will show the free disk space.

Either low memory or low diskspace could cause the issue you describe, but it also could be a firefox specific problem.

---

### Post by Bigneil on 2011-05-30
Hello, thanks for your reply.

the laptop is a dell D630 with a duel core processor and 2 GB ram...surely it can handle Google images.


Here is the results.

---

### Post by Bigneil on 2011-05-31
A friendly little nudge.

I also realized that i forgot to re-enable the medibuntu and non-free stuff after upgrading, FF was replaced by the non-Free version, but the broblem still persists.  

Any ideas?

---

### Post by wildmanne39 on 2011-05-31
> **Bigneil said:**
> I don't know if this is the right subforum for this, but here goes.

I am currently running 11.04 on my laptop. Firefox is struggling to cope with images for some reason. Whenever there are pictures on screen in firefox the computer slows down to a glacial pace.

I tried clearing out the history and cookie files, and i have tried uninstalling and reinstalling FF but the problem still persists.

I have tried other browsers that worked fine with images, but didn't find any that i really liked.

If any of you guys have suggestions on how i can sort it out I'd love to hear them.
Hi, are you using flash for videos or is it required for google that you are using? What video card do you have? or you using the cube or effects? You can log out and click on your user name go to the bottom of the screen and click on ubuntu classic with no effects and see if that fixes it, because that takes less resources and there is no chance of compiz or something like that causing probelms.

---

### Post by Bigneil on 2011-05-31
Thanks for your reply. 
 I am running the non-free version of flash that i copied and pasted from the "troubleshooting" section of the "multimedia how to" sticky thread. 

 I tried your suggestion and started up into classic with no effects, but the problem still persists.

 I have just installed 10.04 along side 11.04, and everything is is working just fine in 10.04, which rules out a hardware problem. 

 I think i may have to back up my home folder and try a fresh installation of 11.04 and see if it still plays up, unless anybody has any more suggestions for things i could try.

---

### Post by linuxinstalledfromhdd on 2011-05-31
What kind of computer did you install this to? What are the general specifications hardware, etc..  How old is it?  Have you done any repairs on it since you bought it?  Anything you can think of to add to this to help with trying to find a solution would be very helpful too. :)

---

### Post by Bigneil on 2011-06-01
> **linuxinstalledfromhdd said:**
> What kind of computer did you install this to? What are the general specifications hardware, etc..  How old is it?  Have you done any repairs on it since you bought it?  Anything you can think of to add to this to help with trying to find a solution would be very helpful too. :)

It is a Dell D630 laptop. 

Intel(R) Core(TM)2 Duo CPU T7250  @ 2.00GHz, L2 cache 2048 KB.
2 GB RAM
NVIDIA Quadro NVS 135M, Video Ram 256 MB, GPU frequency 169 Mhz.

I bought it pre-owned, but tested and refurbished.
I am not convinced that the issue is hardware though.

---

### Post by Thewhistlingwind on 2011-06-01
See if it's the profile first.

1. Close firefox
2. In terminal, run firefox -ProfileManager
3. Make a new test profile and use it.
4. See if problem persists.
5. Report back.

---

### Post by Bigneil on 2011-06-05
> **Thewhistlingwind said:**
> See if it's the profile first.

1. Close firefox
2. In terminal, run firefox -ProfileManager
3. Make a new test profile and use it.
4. See if problem persists.
5. Report back.

thank you for replying.  I tried this excellent suggestion, but alas, still no joy.

i think i will just try a clean install next time i have some time free.

---

