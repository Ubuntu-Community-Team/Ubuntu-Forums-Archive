---
title: "mouse freezes, then system freezes, in several linux distros"
date: 2011-01-08
forum: General Help
---

### Post by RoundTower on 2011-01-08
Hi

I hope this is the right place for this question.  I can't find anyone else on the web who has had the exact same problem.

I have been trying to install Linux as a dual boot option on my 3 year old Dell desktop.  It runs Windows XP SP3 with practically no problems.  Some time (minutes or sometimes hours) after startup in Linux, the mouse pointer freezes.  Everything else seems to work, I can use the keyboard to access the top menu or a terminal.  However, some time (usually minutes) after this, the keyboard also freezes and I can't do anything but turn the power off.

Some observations:

this happens in Ubuntu 10.04 LiveCD, Ubuntu 10.04 installed on my HD, Ubuntu 10.10 installed on my HD, and Mandriva 2010 One, which I believe has KDE and not gnome.  I have never had any problems like this in Windows XP on this computer.  I can't be 100% certain all the symptoms were the same on all the distros, but definitely the mouse froze on all of them.  10.04 Lucid is what I ideally would like to run, but I was willing to settle for something else if it was a Lucid-specific problem.

I replaced the mouse, and it still happened.  Both were wired USB mice, I haven't got a PS/2 mouse to compare.

The LED on the mouse stays lit even after the system is totally frozen.

I **think** I have heard HD activity after the freeze.

The computer is a fairly standard 2007 Dell Dimension (I think), I replaced the graphics card with an ATI radeon x550 and maybe I upgraded the RAM to 3GB but otherwise it is as I got it.  As far as I can see, other USB peripherals (headphones, wireless modem) work fine. 

Usually the problem seems to happen when I am doing something.  If I start up and leave the computer idle for a few hours, it will work fine when I come back (but might fail 10 minutes later).

Any ideas?

---

### Post by dcstar on 2011-01-08
> **RoundTower said:**
> 
........
Usually the problem seems to happen when I am doing something.  If I start up and leave the computer idle for a few hours, it will work fine when I come back (but might fail 10 minutes later).

Any ideas?

Linux pushes the hardware to its limits in a manner Windows does not, so something that may survive under Windows cannot handle the extra demands Linux imposes.

Check CPU/MB temperatures closely and also remove the "new" RAM and see what happens.

---

### Post by RoundTower on 2011-01-10
I installed lm-sensors and sensors-applet: it shows two temperatures Core0 and Core1 which I assumed were CPU temperatures, but "sensors" claims they are on a PCI adapter.  Does this mean they are on my graphics card, or could they be CPU core sensors?  They never seemed to get above 40 Celsius (104 F).

I didn't mean to imply that it crashed during CPU-intensive tasks, usually just loading a webpage or installing an update.  I haven't been gaming or photo editing or even watching video.  System Monitor does show CPU use getting quite high before the crash though -- why should it take 95% of my CPU capacity to load a webpage?

I also tried the system without the "new" RAM and without the graphics card, same happened.  (I had a strong suspicion it was related to the GPU, but apparently not...)

any idea what is going wrong here, or how I can find out more?  Can I force Linux to take it a little easier on the CPU?

Also, please tell me if there is somewhere better I should post this.  I know it's not technically an ubuntu problem, so there may be a more appropriate forum I don't know about.

---

### Post by RoundTower on 2011-01-11
Update: Still having the same issue.  I've replaced or removed every component except the HDD and the keyboard, and I don't think it's either of those.  I'm going to write it off as some problem with the processor or motherboard that just doesn't want to play nice with Linux, and keep this machine Windows-only for another while.

---

### Post by RoundTower on 2011-02-14
solved by updating the BIOS

---

### Post by clhsharky on 2011-02-14
RoundTower


Good to here your success,thanks for posting back to help others.


Sharky

---

