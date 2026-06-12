---
title: "Glxgears not showing FPS"
date: 2009-11-28
forum: General Help
---

### Post by Raffles10 on 2009-11-28
Since installing Karmic x86_64 glxgears no longer prints fps:

ubuntu 9.10
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
33750 frames in 5.0 seconds
34524 frames in 5.0 seconds
33937 frames in 5.0 seconds
34528 frames in 5.0 seconds

Mint 8 (ubuntu 9.04)
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
34156 frames in 5.0 seconds = 6831.169 FPS
28867 frames in 5.0 seconds = 5773.310 FPS
35831 frames in 5.0 seconds = 7166.160 FPS
35847 frames in 5.0 seconds = 7169.261 FPS

I found this bug report:

[Bug #449263]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/449263")

Which says:

> Too many people were abusing it in bug reports. They got confused that since it prints 'fps' that it must be a performance benchmark, which it is not. Removing the fps calculations is to stop the misuse.

Are they serious ? Does anyone using Karmic get a fps printout ? If it has been removed this is treating Ubuntu users like children. Do they think that no Ubuntu users are intelligent enough to know the difference between glxgears and proper benchmarking tests ? :shock:

---

### Post by Zoot7 on 2009-12-03
My understanding was that the new version didn't print the FPS value, never thought about it much.

---

### Post by StuartN on 2009-12-03
There is an awful lot of heat and frayed tempers amongst the ATI Linux driver crowd, who are upset that their own tool "demonstrates that the open source driver sucks".

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark) is moderate, but there is a lot more if you search for "glxgears is not a benchmark" (7,820 hits).

---

