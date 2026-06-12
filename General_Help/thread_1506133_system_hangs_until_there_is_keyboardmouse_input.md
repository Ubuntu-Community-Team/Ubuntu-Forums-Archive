---
title: "system hangs until there is keyboard/mouse input"
date: 2010-06-10
forum: General Help
---

### Post by DrSpaceman on 2010-06-10
I have tried both Ubuntu 10.04 and Xubuntu 10.04. Both have the same issue. currently I'm on Xubuntu. The computer is a Gateway W650 laptop.

At random points, the entire system will hang until I move the mouse or hit a key. At that point, things resume as if they had continued in the background. 

I notice this mainly in music, video, and programs with progress bars. The music or video will just start skipping/repeating until I move the mouse. Progress bars will stop moving and then jump forward when I move the mouse.

While the progress bars are only a minor annoyance, the problems with media are very problematic. I woud really appreciate any help in solving this.

Thanks

---

### Post by dvlchd3 on 2010-06-10
Sounds like a graphics card driver problem.  Do you have any restricted drivers to enable for the graphics? (System -> Administrator -> Hardware Drivers)

---

### Post by DrSpaceman on 2010-06-10
I have proprietary ATI drivers enabled. The driver is called "ATI/AMD proprietary FGLRX graphics driver".

I have the problem regardless of whether I enable or disable the driver.

---

### Post by DrSpaceman on 2010-06-10
After doing some more research, I found some others with similar issues.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=861393](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=861393)

[http://ubuntuforums.org/archive/index.php/t-1358228.html](http://ubuntuforums.org/archive/index.php/t-1358228.html)

Both threads suggest setting nohz=off as a boot option

I added that to the grub.cfg and everything has been fine since. I guess it was a problem with "dynamic ticks".

---

