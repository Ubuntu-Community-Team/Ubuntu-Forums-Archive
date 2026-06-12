---
title: "GRUB overrides boot sequence?"
date: 2009-10-16
forum: General Help
---

### Post by Norami on 2009-10-16
I've been having an issue with booting from CD. No matter how I set the boot sequence in the BIOS, my system always boots my first hard drive with Ubuntu on it. The only way I can get the system to boot from CD is disconnecting that hard drive. I've been talking to Gigabyte about the issue, but the only two things they could come up with was A) Defective board or B) Grub forcing it to boot the hard drive first. I've never heard of this issue before, so I thought I'd throw it out here to see if it's happened before, or if anyone knows how to possibly fix it. I hope it's not a defective board, cause this is the second one that would supposedly be defective.

---

### Post by justleen on 2009-10-16
when starting the system, it will look for bootable devices in the boot order specified.
If the cdrom is first, but cant anything bootable there, it will go on.

Grub will not "overrule" the boot order, but I suspect it wont boot from cd, then goes onto the grub on your HD.

Can you boot other discs at all?

---

### Post by Norami on 2009-10-16
That's where things get tricky, no matter what, when I have my main HD plugged in, it boots to that. Even if I have a bootable CD or USB drive. When I disconnect the main HD, then the boot sequencer seems to work just fine. I have boot discs for Ubuntu Studio 9.04, 8.10, Ubuntu 9.04, Fedora 11 and Mac OSx86, but they all get the same results. Weirdest thing I've seen.

---

### Post by justleen on 2009-10-16
Do you have a "boot selection menu" when booting? Does that do the same thing?

---

### Post by yanceypd on 2009-10-16
Do you by any chance have a multimedia device ie flashcard reader installed.  If so you may have to disconnect the device from the motherboard.  my bad if your using a laptop.

---

### Post by justleen on 2009-10-16
> **yanceypd said:**
> Do you by any chance have a multimedia device ie flashcard reader installed.  If so you may have to disconnect the device from the motherboard.  my bad if your using a laptop.

+1 one on that.. make sure you have no flash cards in the drive, if you have a reader..DOnt think you'll have to disconnect from the main board, just make sure there is no flashcard in it

---

### Post by Norami on 2009-10-16
This is a system I built a few months ago. S no flash card reader. All I've got is 2 harddrives and a CD/DVD drive. There's a firewire card in it, but nothing connected.

I don't get any boot selection menu. It goes from post, straight to Grub. If I disconnect the main hard drive, THEN it asks me if I want to boot from CD.

---

### Post by PrePenguin on 2009-10-17
The bios supercedes before ubuntu's MBR even gets read so something is definately funny with the hardware like a incorrect jumper setting on the Motherboard or something. Also does the bios have like HD monitoring on it that is used to monitor a drive such as like SMART etc?

---

