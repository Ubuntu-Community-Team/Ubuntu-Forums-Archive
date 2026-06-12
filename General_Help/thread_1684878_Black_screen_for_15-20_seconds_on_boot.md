---
title: "Black screen for 15-20 seconds on boot"
date: 2011-02-09
forum: General Help
---

### Post by maxpower87 on 2011-02-09
I'm experiencing an odd issue on my Acer Aspire One netbook [AD260]. Specs:

Intel Atom N450 proc
2GB RAM
Intel Graphics Media Accelerator 3150
250GB HDD.

I have BURG set up to triple boot into Windows 7, Ubuntu 10.10 and Chromium OS.

Booting into windows is fine no problems at all. However booting into Ubuntu (and Chromium btw) results in a black screen for approx 15-20 seconds. During this time I can hear the start-up sound on both Ubuntu and Chromium but the screen is black (although if I look really hard I can barely make out the logon screen with my username, waiting for me to enter a password - so it is almost as if the screen is dimmed by an incredible amount).

After 15-20 seconds the screen brightens back to normal and i can see the logon screen clearly. This is quite annoying as technically I should have already been in the process of logging on. The reason I installed Ubuntu and Chromium is to decrease boot up time but it seem like its a graphics issue of some sort that dims the screen on logon right after BURG.

Any ideas??

---

### Post by jenaniston on 2011-02-09
I almost always remove "quiet' from the kernel arguments (near the end of line before splash) just to see ***all*** of what is *really* going on (behind the scenes/screen ) during boot up . . .
you'll see plenty probably!
 
Good luck.

---

### Post by maxpower87 on 2011-02-09
> **jenaniston said:**
> I almost always remove "quiet' from the kernel arguments (near the end of line before splash) just to see ***all*** of what is *really* going on (behind the scenes/screen ) during boot up . . .
you'll see plenty probably!
 
Good luck.

removing quiet from kernel arguments has no effect :( still get the same issue.

---

### Post by jenaniston on 2011-02-09
plenty of RAM (which I *wouldn't* be used to) 
 
so, driver problem ? . . . 
I run/test alot of USB drives (live and full USB drive installs) 
to use on different university computers than what the original install to the pendrive was with -
so I am use to seeing the extra work for searching for hardware configuation.
 
. . . sorry, that's the only ideas I got.

---

### Post by maxpower87 on 2011-02-09
im not sure whether its a driver issue as the screen is fine after approx 20 seconds or so.

this is the timeline:

boot to burg/grub2 - 5 seconds
select Ubuntu - 1 second
Ubuntu purple splash with dots - 3 seconds
black screen (normal loading) - 5-8 seconds
Ubuntu logon drums 
HIGHLY DIMMED SCREEN (almost non-visible) but can barely see logon menu - 15 seconds

the problem is that everything boots normally but its as if the display is super dimmed until about 15 seconds after the logon screen has appeared.

---

### Post by maxpower87 on 2011-02-10
okay, looks like it is definitely a driver issue. I have changed the driver to "fbdev" in xorg.conf and it seems to have resolved the issue in Ubuntu.

Sucks that intel drivers don't work properly..

---

