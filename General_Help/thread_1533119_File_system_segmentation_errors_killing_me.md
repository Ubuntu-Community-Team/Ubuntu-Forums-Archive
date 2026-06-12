---
title: "File system segmentation errors killing me"
date: 2010-07-17
forum: General Help
---

### Post by complience on 2010-07-17
I've installed ubuntu on a new build

I've tried with both Karmic and Lucid, 32bit and 64bit

All my applications randomly crash, (firefox, chrome, mythtv, gedit, aptitude)

core motherboard drivers (sound, bluetooth) will sometimes be undetectable - requiring a restart to magically fix.

Looking the logs, there are error messages regarding file system segmentation faults - see the log below for a sample.

What could be causing my file system to become corrupt?
I cant fix this!

---

### Post by prodigy_ on 2010-07-17
AFAIK, [segmentation faults are related to RAM](http://www.cyberciti.biz/tips/segmentation-fault-on-linux-unix.html), not to file system. So first of all you should check your RAM with memtest or with some other diagnostic tool (I can recommend [MPrime](http://www.mersenne.org/freesoft/) which is very sensitive to memory instability).

---

### Post by iponeverything on 2010-07-17
My guess would be that something mis-configured in your bios. Bad memory timing maybe. Try changing to the bios defaults. 

Also check or change out the cable going to the hard drive and and make sure that all the cards are correctly seated. 

Also make sure that the system has good a ground, it might be grounding out though one of your peripherals.

---

### Post by complience on 2010-07-17
A memory problem would certainly explain the apparent random crashes effecting all the applications.

When I first put together this build I did a memory check and it came back showing a fault - so i swapped out the memory for new sticks again.

There are errors in the logs on restarts regarding memory - ive attached what i think could be relevant but its fairly complex stuff.

---

### Post by complience on 2010-07-18
removed 1 stick of ram and turned on ecc - havent crashed recently.. looking good

---

