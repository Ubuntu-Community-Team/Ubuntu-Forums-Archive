---
title: "Youtube videos skin color displays as blue"
date: 2012-04-08
forum: General Help
---

### Post by rapattack1 on 2012-04-08
Hi for some reason i have noticed int he last few days that any youtube video that has people in it their skin color is blue. Is there a way to correct this? In the thumbnails at the right of any youtube page every color seems normal but the playable video like this one [http://www.youtube.com/watch?v=KzjMIcER4EU](http://www.youtube.com/watch?v=KzjMIcER4EU)
I can do a capture if that helps of what i am seeing

---

### Post by howefield on 2012-04-08
Try the solutions in this thread..

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by westie457 on 2012-04-08
Hi the info here might be of some use to you. [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by rapattack1 on 2012-04-08
Thanks howefield that first solution by clicking the video and changing the hardware acceleration setting did it...yippee! Your a gem :))

---

### Post by gnusci on 2012-06-01
Here another solution for Oneiric or Precise, install patched libvdpau:

$ sudo add-apt-repository ppa:tikhonov/misc
$ sudo apt-get update
$ sudo apt-get install libvdpau1

Works for me.

---

