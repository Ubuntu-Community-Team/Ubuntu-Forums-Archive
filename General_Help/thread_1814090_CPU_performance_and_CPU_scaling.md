---
title: "CPU performance and CPU scaling"
date: 2011-07-28
forum: General Help
---

### Post by sam.petrocelli on 2011-07-28
I have been using Ubuntu for a couple years now.  I primarily use it for writing software for my robotics research.  If I have my laptop plugged in, it operates much faster than when it using just the battery (ie not plugged in).  (which is all normal of course) So I checked my bios and there are no settings for what the computer (cpu) should do when only battery power is available.  Ok.  So I used the CPU scaling panel tool.  I added a cpu "scaler" for each of my two processors and set them both for performance.  I ran some image processing code and it executed in 260ms with the computer plugged in.  Then I disconnected the power from my laptop, checked that the cpu clock was still on performance, and ran the same process.  This time it took almost 500ms to execute.  (In both instances the process ran several times just to make sure the execution times were consistent)  I even checked /proc/cpuinfo and it showed that both cores were maxed at 1.8GHz.  There must be something else that is limiting the processing, which I just don't know of.  Any ideas?

My laptop is a Sony Vaio VGN-FZ140E with an Intel(R) Core(TM)2 Duo T7100  @ 1.80GHz CPU.  Thanks for your help and your time.

---

