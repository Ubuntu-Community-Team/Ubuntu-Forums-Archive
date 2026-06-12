---
title: "Ubuntu locks up, trying to fix"
date: 2009-11-29
forum: General Help
---

### Post by IllegalCharacter on 2009-11-29
I had a nicely working Jaunty install going for a while, however one day it decided to start randomly freezing. The system will work fine for about 5 minutes, but then after that it is just completely locked up, and you can't do anything but a hard restart.
Trying to boot off the Jaunty LiveCD produces the same result, just completely freezes.
Trying to boot off the Karmic LiveCD doesn't actually work, the system just hangs at a black screen for an hour.

I know the computer still works since Windows works fine. One issue though is that the ext3 driver that I installed in Windows is no longer able to access the Ubuntu partitions.

I have no idea where to even begin fixing this problem. Any pointers?

---

### Post by IllegalCharacter on 2009-12-04
*bump*

---

### Post by ed-koala on 2009-12-04
The Live CD freezing suggests a hardware issue. Especially since you say it worked fine before. Though, not sure why Windows would work. Still, computers do funny things. I'm wondering if some sort of hardware failure occurred that affects Ubuntu but not Windows. Is that possible?

---

### Post by IllegalCharacter on 2009-12-04
Yeah I've been thinking it is a hardware issue. I thought it might be the video card, although I can play 3D games no problem under Windows so I don't think it is compiz causing the problems.

I'll try using the 32-bit LiveCD and/or a Fedora LiveCD to see what happens.

---

### Post by IllegalCharacter on 2009-12-05
Darn, tried using the 32-bit version *and* the Fedora LiveCD, both locked up. Tried unplugging the hard drive, same issue occurs. Memtest worked fine, gave no issues.

Guess this doesn't help anyone here, but if you have some insight it would be much appreciated ;)

---

### Post by NoaHall on 2009-12-05
It's probably your CPU/graphics card then.

---

### Post by IllegalCharacter on 2009-12-05
Do you know how I'd go about testing those?

If it is the CPU or graphics card then it'd be weird that Windows would work fine even while playing graphic-intensive games without a hiccup. And it's not the 64-bit part of Ubuntu because 32-bit Ubuntu crashes all the same.

---

### Post by fluffman86 on 2009-12-05
Boot into Windows, download unetbootin, and "burn" the iso you have onto a USB stick.  Maybe your CD burner isn't burning properly.  If you can't boot from USB, then go to a friends computer, download the plop boot cd, and burn it there using the *SLOWEST* settings possible to prevent errors.

---

### Post by IllegalCharacter on 2009-12-06
Nah it's the same deal with the USB boot. It fires up into Ubuntu for a minute or so, I'm able to do things like open Firefox or whatever, but then it just freezes completely. I'm not even able to switch to a console with Ctrl+Alt+F1 or anything.

I also tried running some different kernels that had been installed, didn't change anything.

I'm going to run some diagnostics from Windows and see what happens.

---

