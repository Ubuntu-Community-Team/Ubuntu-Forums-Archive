---
title: "troubleshooting guide for ubuntu?"
date: 2011-11-09
forum: General Help
---

### Post by cybern8 on 2011-11-09
is there a good how-to guide with tips on how to troubleshoot ubuntu hangs, crashes, and device issues? i.e., which logs to look at when, enabling diagnostic tracing or monitoring to capture more detail, etc.

i have a couple of issues i hit regularly in my ubuntu 10.04LTS environment running on ibm thinkpads, and have been searching for answers and am at a loss on how to dig deeper into the problems.

here are the two issues for which i'd welcome some advice on how to debug:

issue 1 - system will just hang/stop; i have to physically power off the machine and power on again to recover.

* i have checked the system logs, but can't find any entries or messages to help me understand what is causing the issue.

issue 2 - on every boot, the system is running fsck on my hard drive. i cannot figure out why this is happening. i do notice some messages that appear briefly on the console when i do a 'shutdown' that -may- have something to do with the system not unmounting the drive, but they don't stay on the screen long enough for me to read them. i even tried using the camcorder on my phone :) to record the image when i shutdown so i can try to view it and freeze the frame, but the image quality is too poor.

* again, i haven't been able to find anything useful in the logs but maybe there is a specific log i should be checking that i don't know about.

adv-thanks-ance, ubuntu gearheads!

---

### Post by techvish81 on 2011-11-09
run a disk health check with any such utility,  u can try the default disk utility which comes with Ubuntu,  I haven't tried it yet, but on what u r saying, there could be some problem in your drive.

---

