---
title: "HannStar Display Corp HN198D blinking on cold boot"
date: 2012-09-30
forum: General Help
---

### Post by alan21276 on 2012-09-30
I've had this problem for a few weeks now and I'm having trouble pinpointing the cause of it.
Here is my set-up

HannStar Display Corp HN198D monitor
ASUS M2NPV-VM motherboard with NVidia GeForce 6150 GPU
AMD Athlon 64 X2 Dual Core Processor 3800+ × 2 

NVIDIA Driver Version 304.51

I'm running ubuntu 12.04 with Kernel Linux 3.2.0-31-generic-pae

When I do a cold boot (from power off) my monitor tries to start but within a few seconds it powers off, then restarts again and powers off again.....it cycles like this indefinitely until I do a hard power off.
I can only get it to work properly after about a dozen or so restarts of the system interrupting it at various different stages of the boot process.
I have quiet start and nomodeset in my grub settings and I have tried different combinations of boot and grub settings all with the same result.
I've also tried resetting my BIOS to factory defaults...no luck with that either.
I know my monitor works as I've tested it on another system.

The operating system is starting up in the background.....just seems to be a video output issue.
It worked perfectly with ubuntu 10.04, and with 12.04 until recently......I'm sure it was an update that broke things.
If I do a software reboot it shuts down and restarts perfectly, it only seems to happen on a cold boot.
Also if my screen switches off via power saving it has the same problem when I try to wake it.
In the mean time I've set it to never sleep and leave the system running 24/7, but I don't like leaving things powered up when I'm not at home for safety reasons.

Google searches haven't turned up anything.

Has anyone had this type of problem before?

Any suggestions on how to fix it or pinpoint the cause of it?

Any help will be much appreciated.

---

### Post by alan21276 on 2012-10-01
bump

---

### Post by alan21276 on 2012-10-15
1 more bump

---

### Post by alan21276 on 2012-12-02
> **alan21276 said:**
> I've had this problem for a few weeks now and I'm having trouble pinpointing the cause of it.
Here is my set-up

HannStar Display Corp HN198D monitor
ASUS M2NPV-VM motherboard with NVidia GeForce 6150 GPU
AMD Athlon 64 X2 Dual Core Processor 3800+ × 2 

NVIDIA Driver Version 304.51

I'm running ubuntu 12.04 with Kernel Linux 3.2.0-31-generic-pae

When I do a cold boot (from power off) my monitor tries to start but within a few seconds it powers off, then restarts again and powers off again.....it cycles like this indefinitely until I do a hard power off.
I can only get it to work properly after about a dozen or so restarts of the system interrupting it at various different stages of the boot process.
I have quiet start and nomodeset in my grub settings and I have tried different combinations of boot and grub settings all with the same result.
I've also tried resetting my BIOS to factory defaults...no luck with that either.
I know my monitor works as I've tested it on another system.

The operating system is starting up in the background.....just seems to be a video output issue.
It worked perfectly with ubuntu 10.04, and with 12.04 until recently......I'm sure it was an update that broke things.
If I do a software reboot it shuts down and restarts perfectly, it only seems to happen on a cold boot.
Also if my screen switches off via power saving it has the same problem when I try to wake it.
In the mean time I've set it to never sleep and leave the system running 24/7, but I don't like leaving things powered up when I'm not at home for safety reasons.

Google searches haven't turned up anything.

Has anyone had this type of problem before?

Any suggestions on how to fix it or pinpoint the cause of it?

Any help will be much appreciated.






SOLVED..................monitor was knackered, new one fixed the problem.

---

