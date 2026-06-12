---
title: "persistent lockups with 9.04"
date: 2009-07-08
forum: General Help
---

### Post by princesshammer on 2009-07-08
I upgraded to 9.04 recently, and have been experiencing regular lockups, requiring a hard reset. I suspect it's something related to usb or video. I was seeing lockups every few minutes, until I added "noapic" to the boot. That helped, but it still locks up many times a day. I've noted that many of the times it locks up, it's either after I've been away from the console for awhile (perhaps some power management issue?), or while I'm dragging a scroll bar with the mouse (video? usb?). Or it could just be that I do those things a lot, and the lock-ups are random.

The video card is a GeForce FX 5200. I'm using the non-free nvidia driver, nvidia-glx-173, 173.14.16-0ubuntu1. CPU is AMD Athlon(tm) XP 2600+. I use two usb mice.

Nothing in the system logs looks suspicious to me, though I wouldn't necessarily know what to look for.

Anyone have a clue?

---

### Post by combatwombat_nz on 2009-07-08
Tried running it for some time ONLY on the live CD? That will tell you if the problem is harddisk based. 
Have you run the MEMTEST on the live CD?
Have you checked your video card's fan to make sure it is dust-free, and spinning nicely? Check the CPU fan too.

---

### Post by Jebtrix on 2009-07-08
I've locked up windows machines with flaky onboard usb already. Get a PS2 mouse (if you can use one) and disable onboard USB to see if there is any difference. Or disable onboard and get a cheap USB 2.0 PCI multiport addon card instead.

---

### Post by Jebtrix on 2009-07-08
Do you anything else installed? SCSI card, soundcard, etc? Combatwombat is right, always test memory and basics first. Use HD manufacturers diagnostic software to test HDs. Then do process of elimination. Take all PIC cards out except what you need ie video. Disable onboard sound, usb, etc.

---

### Post by princesshammer on 2009-07-16
The memory test on the live CD crashes immediately. I tried bumping up the voltage +.2V on the memory. That seemed to make it more stable. It was crashing every 20 min, or so, yesterday. After increasing the voltage it ran the rest of the day, but crashed sometime in the night.

The memory test still won't run, with the voltage bumped up. Since it doesn't even get off the ground, I suspect it has some unrelated problem.

It was unstable on the live CD, too, so probably not a disk problem. The live CD uses the free video driver, so that eliminates the non-free nvidia driver as a problem.

I've had this machine for a few years, and this instability just appeared. Something is wearing out, I guess... memory, fans, power supply. I installed lm-sensors, and sensorsd, but nothing really jumped out as problematic. I doubt the labels are correct, but MB, CPU, and "other" temp are 44C, 41C, and 64C.

---

