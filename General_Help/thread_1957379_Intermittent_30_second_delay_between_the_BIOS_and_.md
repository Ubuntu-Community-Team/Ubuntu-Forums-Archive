---
title: "Intermittent 30 second delay between the BIOS and the HD booting on Asus B53J laptop"
date: 2012-04-12
forum: General Help
---

### Post by webcrawler42 on 2012-04-12
I have an intermittent 30 second delay between the BIOS and the hard drive booting (seeing the blinking cursor of GRUB) on my ASUS B53J laptop.  During this 30 seconds the hard drive light does not flash at all. The problem will sometimes only happen once every two weeks, or sometimes a few times a week.  I am running Ubuntu 11.04 (natty). Synaptic says "GRand Unified Bootloader, version 2 (PC/BIOS version)" is at version "1.99~rc1-13ubuntu3", which is the latest version.

I have tried resetting the BIOS to optimal settings as well as changing a few of the settings (I can list out exact ones if requested). I have also tried changing a few of the Intel ME/AMT settings that are displayed after the BIOS. I have tried checking the S.M.A.R.T. of the hard drive, which showed no errors.  I also ran Memtest86, which also showed no errors.  No hard drive clicking, and my CPU and HD temps are normal.  There is no BIOS update for my laptop.

Any suggestions?

---

### Post by roelforg on 2012-04-12
Maybe the bios periodically is performing an intergrity check on the bios-rom?

---

### Post by webcrawler42 on 2012-04-12
From this [link]("http://security.stackexchange.com/questions/3786/how-to-check-the-integrity-of-my-bios") it seems like the TPM (trusted platform module) would be responsible for such a check.  I have tried disabling the TPM and still experienced the intermittent 30 second delay.

Is there any way to see if it is being checked or what settings would effect such a check?

Another bit of information.  The boot sequence is as follows: BIOS->Intel ME/AMT->(30 second delay or not)->blinking cursor of GRUB.

---

### Post by cloyd800 on 2012-04-13
Just FYI, and I'm not sure this will help any but it's a long shot at least.

I had this exact same issue on a work laptop of mine, I found that it was due to having ANYTHING plugged into a particular USB slot, regardless of it just being a USB cable or an actual device.  Removing the USB cable when booting up resolved the delay and allowed the computer to continue booting.  Once the OS loaded successfully, I could reinsert whatever USB device I had previously hooked up back into the USB slot and it worked as intended.

---

### Post by webcrawler42 on 2012-04-13
Thank you for the suggestion, but I don't have anything plugged into the usb ports (aside from what is wired internally since it is a laptop).

---

### Post by webcrawler42 on 2012-04-18
I have tried replacing the RAM with some known good RAM and expreienced the same intermittent delay, so I believe the RAM is not the problem.

I also put a bootable CD in the drive and was able to get theintermittent delay before the CD would boot, so I don't think the problem is the hard drive.

---

