---
title: "Odd graphical issue."
date: 2009-08-31
forum: General Help
---

### Post by ament001 on 2009-08-31
I have been using the latest version of ubuntu for a little while now on my laptop without any real problems, until today that is. I booted up my laptop and it never reaches the user login, it just loads up to this screen. [IMG]http://i25.tinypic.com/idfvbs.jpg[/IMG] I have some files that I would really like to not lose on the computer, if anyone can help me out I would appreciate it.

---

### Post by NoaHall on 2009-08-31
Can you boot into recovery mode?
What is your graphics card? Do you have a on board one/spare one?

---

### Post by ament001 on 2009-08-31
I get this exact same screen no matter how I boot up, normal, or recovery. Unless I'm going about it the wrong way. The GPU is a Radeon Xpress 200m, and since it is onboard, not much I can do about it. Its my old laptop.

---

### Post by NoaHall on 2009-08-31
Try using 8.04.. .. Or using the live disk to boot in and save your data, then reinstall.

---

### Post by ament001 on 2009-08-31
I've tried getting into my files using live disk but the folder I need to get at says I do not have the file permissions. I can get to that mid point in the recovery mode where I am given a bunch of options like checking the disk and such, is there anythingI can do from there like resetting the graphic driver from the command prompt or something?

---

### Post by hockeytux on 2009-08-31
You installed the wrong drivers and need to delete them.

This thread should solve your problems: :)

[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640)

---

### Post by ament001 on 2009-08-31
> **hockeytux said:**
> You installed the wrong drivers and need to delete them.

This thread should solve your problems: :)

[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640) That appears to be the same issue I have, thank you very much.

---

### Post by hockeytux on 2009-08-31
No probs :popcorn:

---

### Post by Johnny B on 2009-08-31
boot the recovery mode and:

# sudo apt-get remove xorg-driver-fglrx

---

