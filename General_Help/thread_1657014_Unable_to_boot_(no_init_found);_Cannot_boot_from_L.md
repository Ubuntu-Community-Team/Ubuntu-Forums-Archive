---
title: "Unable to boot (no init found); Cannot boot from Live CD (10.10)"
date: 2010-12-31
forum: General Help
---

### Post by bjnueva8623 on 2010-12-31
I've been dual booting 10.10(with Windows7) for about a month. Today is the first time I've encountered a serious problem. 

This morning, nothing functioned properly after trying to open up several programs. The computer seemed to be "frozen", although the mouse was working fine. 

I decided to reboot, but then encountered an even bigger problem. It failed to boot and got this message:

> **no init found. try passing init= bootarg**

I searched the forums and found a solution, I think. The problem now is that it requires a Live CD session and I keep getting this:

> **GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)**

In case it matters, I didn't install 10.10 from an ISO, I just upgraded from 10.04. Is there a solution for this problem?

---

### Post by Rubi1200 on 2010-12-31
Hi,
it could be that the CD is damaged or the data on it was somehow corrupted.

Try downloading and burning another copy and see if that helps.

---

### Post by bjnueva8623 on 2010-12-31
Hello, 

I made a new copy as you said, but still no luck. Same problem persist.

---

### Post by bjnueva8623 on 2010-12-31
Bump.

I'm not against doing a complete reinstall of 10.10, but I'm worried about that "**no init found. try passing init= bootarg**" problem. What causes it exactly? Is it just a major bug? I wouldn't want to do a fresh install only for this to happen again.

---

### Post by bjnueva8623 on 2010-12-31
Well, I just failed on my 3rd attempt. 3rd Live CD; similar unsuccessful results. Instead of getting the "GLib-WARNING", it just stayed on the boot screen (or is it called splash screen?) for close to an hour before I gave up and shut it off. Has this happened to anyone before? I'm getting a bit frustrated. HELP!:(

---

### Post by bjnueva8623 on 2010-12-31
Can someone at least confirm that there is no solution and that I should just do a clean install?

---

### Post by Rubi1200 on 2011-01-01
What graphics card do you have?

Did you try recovery mode or an older kernel?

---

### Post by bjnueva8623 on 2011-01-01
I have a Radeon HD 5450 and yes, I have tried older kernnels and recovery mode. I still get "no init found. try passing init= bootarg". Could it be that my HDD has crashed?

---

### Post by nwa malaysia on 2011-01-01
i'm having the same problem actually. ubuntu got stuck and after reboot, same message appears. Then I tried download ubuntu from live cd and it got stuck during installation.

---

### Post by nwa malaysia on 2011-01-01
maybe this could help,

[http://ubuntuforums.org/showthread.php?t=1244466&page=2](http://ubuntuforums.org/showthread.php?t=1244466&page=2)

and this

[http://ubuntuforums.org/showthread.php?t=424292](http://ubuntuforums.org/showthread.php?t=424292)

I'm trying both anyway

---

### Post by bjnueva8623 on 2011-01-01
Hmm, perhaps I'll try a slower speed when burning the ISO. Thanks, nwa malaysia.

---

### Post by bjnueva8623 on 2011-01-01
Double post, sorry.

---

### Post by Rubi1200 on 2011-01-01
When you put the CD in and boot the computer, as Ubuntu starts to load hit F6 and then Esc to see the kernel boot line.

Use the cursor to move back and delete the words quiet splash. Type nomodeset instead and then Enter to boot.

If that does not help, try with some of the following options:
xforcevesa
radeon.modeset=0
radeon.modeset=1

---

### Post by bjnueva8623 on 2011-01-01
> **Rubi1200 said:**
> When you put the CD in and boot the computer, as Ubuntu starts to load hit F6 and then Esc to see the kernel boot line.

Use the cursor to move back and delete the words quiet splash. Type nomodeset instead and then Enter to boot.

If that does not help, try with some of the following options:
xforcevesa
radeon.modeset=0
radeon.modeset=1

Ok, I tried this and the only one that seemed to work was "xforcevesa", but all it did at the end was show *welcome to ubuntu* and a command prompt.

With the others, it was more of the same (black screen; lots of words), but there was an awful lot of "error", "unable", "failed" etc etc. 

Also, "xforcevesa" and "radeon.modeset=1" had a different aspect ratio than the others.

---

### Post by Rubi1200 on 2011-01-02
Did you try the suggestion of burning at a lower speed?

You should also check the integrity of the disk before burning:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by bjnueva8623 on 2011-01-02
> **Rubi1200 said:**
> Did you try the suggestion of burning at a lower speed?

You should also check the integrity of the disk before burning:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Yeah, I've used 4 disc in total. None have worked. Honestly, I'm just waiting for someone to tell me that my HDD is dead, or that the situation is hopeless. I'm not sure if I'm going to reinstall Ubuntu, because if this is a bug, than it has the potential to happen again. I have yet to find a real solution in the forums. Only on 10.04, but it was just a bug that eventually got fixed supposedly. Nothing for 10.10 yet. I'm surprised by the lack of help. So far, you're the only one who's replied with anything worthwhile. Thanks.

---

### Post by Rubi1200 on 2011-01-02
I think I may have found something that could help.

Firstly, do you have backups of your important data from Ubuntu?

if not, then my first suggestion is to use another LiveCD like [Knoppix]("http://distrowatch.com/table.php?distribution=knoppix") to boot the computer and rescue your files.

Then, if you are willing to try again, here is the solution:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://ubuntuforums.org/showpost.php?p=10169169&postcount=176](http://ubuntuforums.org/showpost.php?p=10169169&postcount=176)

In the second link, forum member mörgæs offers a solution.

---

### Post by nwa malaysia on 2011-01-06
I've solved my problem btw. It has something to do with the hardware, the hard disk to be exact. why dont you run a diagnost test on ur computer. it helps a lot..:)

---

