---
title: "Installing IDE hard drive while computer is running?"
date: 2010-07-06
forum: General Help
---

### Post by DnDer on 2010-07-06
I have wiped a computer using DBAN. The computer no longer boots with the hard drive in it - the screen remains black, and I receive no beep codes.

Is it possible to get 10.04 running, live off a CD, and then physically install the drive inside the case? Would I be able to detect and mount the drive from the live CD?

I'd hate to think I bricked a perfectly good hard drive, but this is a problem I've not encountered before, so I'm not sure where to start for solving it. Is ubuntu magic enough to fix this? Or are there some other recommendations the community might have?

---

### Post by jeebustrain on 2010-07-06
hot-add hardware must first be supported by the bios/motherboard itself. You literally could fry the drive (and the motherboard) by plugging it in while the PC is on if it's not supported. 

that being said, what about if you connect it to a secondary IDE cable or perhaps change the boot order to exclude the HDD while the drive is not attached. Another option would be to put it inside of a USB enclosure and try to reinitialize it that way (on another PC or booting the same PC w/ a live cd).

If that doesn't work and you're not able to get the PC to even POST with the drive attached, I'm afraid you might be SOL.

---

### Post by DnDer on 2010-07-06
The secondary IDE cable is already tied to the CD-ROM.

I disabled the hard drive from the boot priority, and then turn it off to plug the drive in. I did get video, and POST told me that it could not find hard drive 0, prompting me for setup or for continuing on.

I entered the setup and added the hard drive back onto the boot order (at the bottom), and was told again after exiting the setup that the hard drive was not detected. Using the option to continue, I booted using the CD (it has first priority in the boot sequence), and opted to install ubuntu instead of trying it.

I got to the point where it asks me to prepare partitions, and there are no hard drives listed.

An enclosure is something I'll have to look for at home, since I don't have any here. It might be possible to fix it there. But, based on what I've described, does your opinion change about the hard drive's livelihood?

---

### Post by robvas on 2010-07-06
Have you tried swapping around IDE/power cables?

---

### Post by DnDer on 2010-07-06
JEEBUS:

IDE cable #2, in IDE port #2 was plugged to the hdd.
IDE cable #1, in IDE port #1 was plugged into the CD-ROM.

The error message this time says "secondary hard disk drive 0 not found" instead of "primary."


ROBVAS:

Should I put the cables in opposite slots now, as suggested?

---

