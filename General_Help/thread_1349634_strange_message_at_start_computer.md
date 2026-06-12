---
title: "strange message at start computer"
date: 2009-12-08
forum: General Help
---

### Post by Achilles124 on 2009-12-08
I get the following message when starting my computer:
> Intel Core (TM) Duo CPU  E 4600 x 2.4 GHz Speed: 200x12= 2400MHz

Memory Frequency For DDR 800 Mhz single channel 2048 MB

Initializing USB Controllers Done
USB Devices: 1 mouse
Auto-Detecting PRI Master ... Atapi CDrom
Auto-Detecting Pri Slave .... Not Detected
Auto-Detecting Sec. Master IDE ard Disk
Pri Master: TSSTCORP CDDVDW SH- S202H SB00 ULTRA DM mode-5 
   S.M.A.R.T. Capable and status ok

Press del key to enter Setup menu
F11 to enter Bootup Menu

A: Drive Error
Press F1 to resume

I press F1 and the computer starts. The systems starts, so why this errormessage? And what can I do about it to make it disappear? And why the A: Drive Error?

Thanks beforehand

---

### Post by Sef on 2009-12-08
A: Is/Was the floppy drive.  It seems your computer is trying to find it and cannot.  Have you a floppy drive on your computer?

---

### Post by Achilles124 on 2009-12-08
There is no floppy drive on my computer.

---

### Post by TitanusEramius on 2009-12-08
It's sounds like the BIOS is set wrong, but it's hard to say, have you:

Changed some hardware recently?
Had your tower opened (for cleaning maybe)?
Checked the floppy-drive still works in your system?
  (if you have a floppy-drive, off course)


If you enter the bios you have to be very careful, and i would recommend you to read the users guide for the motherboard before entering and make sure you know how to reset the BIOS, just in case.

Te

---

### Post by blueridgedog on 2009-12-08
You need to instruct your BIO to the fact that you don't have an A drive.  It may be under peripherals or drives.

---

### Post by Achilles124 on 2009-12-08
yes, I went into BIOS and pressed "F6 setting to optimal settings.". This I have done when I encountered problems with starting my computer. What can I do to get the previous settings?

---

### Post by Achilles124 on 2009-12-08
Okay, figured it out. I have pressed the Load Fail-Safe Defaults and because I have done that, I got the message I got above. By going into the Standard CMoS Features, I was able to switch the A: drive to not present.

The above message doesn't appear anymore.

---

### Post by Achilles124 on 2009-12-08
And thanks for answering.:D

---

