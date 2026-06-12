---
title: "Black screen after suspend and resume"
date: 2009-08-11
forum: General Help
---

### Post by louisJ on 2009-08-11
Hi 

I just installed Ubuntu Jaunty 9.04 on my laptop Thinkpad t43 (2668WR9).
Everything seems to work fine, but suspend/resume.
Suspend works fine, but when resuming the wifi, disk lights, ventilation are on, but the screen stays black.

Any help would appreciated.

Thank you.

---

### Post by LowSky on 2009-08-11
what video driver are you using? ATI's or the community supplied one?>

---

### Post by Chronon on 2009-08-11
I posted about the same problem just a minute ago here: [http://ubuntuforums.org/showthread.php?t=1237571](http://ubuntuforums.org/showthread.php?t=1237571)

In my case, booting the previous version of the kernel (2.6.28-13) fixes the problem.  

I also posted in this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357073](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357073)

---

### Post by louisJ on 2009-08-11
Hi LowSky
I am new to linux, but as I installed Linux and nothing else, I guess the driver I use is the community supplied one.
I have also tried to install EnvyNG and install the ATI driver, but apart from changing the resolution (to wrong) it doesn't solve the problem.
Should I do otherwise?
Thank you

Hi Chronon
In the boot menu I have the version 2.6.28-11, I tried but it doesn't solve the problem.
How can I boot with the version 2.6.28-13 knowing that I don't have it in the boot menu?
Thank you too

---

### Post by Chronon on 2009-08-13
It was apparently some fluke.  I have now suffered this problem with 2.6.28-{11,13,14}.  It is purely a backlight issue as I can see the screen is rendered properly under proper illumination.  In this way I can log out and the login screen is properly lit.  I don't know that this is consistent, but at least today I have been able to log in and have the backlight continue working.  This isn't much of a workaround since you need quite good lighting in order to see anything with the backlight off.  

Suspend/resume was working basically fine until last week some time.  I say "basically" because I had hiccups with resuming when trying to use Fn + F1 on my Eee PC 1000HEB, but pressing Fn by itself would do the trick.

---

