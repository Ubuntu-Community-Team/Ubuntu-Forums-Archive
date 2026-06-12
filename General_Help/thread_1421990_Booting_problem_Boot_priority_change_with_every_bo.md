---
title: "Booting problem: Boot priority change with every boot after Shutdown"
date: 2010-03-04
forum: General Help
---

### Post by mail.vipinaggarwal on 2010-03-04
Whenever I start my PC, the information of 'First Boot device' in BIOS changes from hard disk to CD-Rom. It happens with new start, I mean, if I restart my computer after resetting First boot device to hard disk, then priority does not change.

Just as I switch on computer, a black screen appears with the message:

CMOS - checksum error - defaults loaded

press F1 to continue, DEL to enter setup

Recently it used to happen, that PC was not reading my hard disk containing GRUB. I have 2 hard disks. I switched the power cables of two hard disks.
After that, both hard disks were shown by BIOS but the above mentioned error started appearing.

Also grub takes too much time to load. It takes almost 20 seconds.
Earlier I was using 'Puppy Linux'. In that, Grub was loading in fraction of second.

Is there any wiring or hardware related issues with my PC?

---

### Post by dcstar on 2010-03-04
> **mail.vipinaggarwal said:**
> Whenever I start my PC, the information of 'First Boot device' in BIOS changes from hard disk to CD-Rom. It happens with new start, I mean, if I restart my computer after resetting First boot device to hard disk, then priority does not change.

Just as I switch on computer, a black screen appears with the message:

CMOS - checksum error - defaults loaded

press F1 to continue, DEL to enter setup

........
Is there any wiring or hardware related issues with my PC?

Try changing the dead CMOS battery on your motherboard.

---

### Post by Pascal11110 on 2010-03-04
Yes, basically your CMOS battery is dead so when your computer shuts off it is not saving your settings. You can just take the battery out and bring it to any radioshack and they can match it for like 3 bucks.

---

### Post by mail.vipinaggarwal on 2010-03-06
Thanks for support!
I have changed battery and checksum error is eliminated now.

But why grub is taking so long (15-20 seconds) to load?
What should I do to make grub loading faster?

---

### Post by mail.vipinaggarwal on 2010-03-06
Hey pascal, please guide me. Does grub normally takes this much time to load?

---

### Post by Pascal11110 on 2010-03-07
Does it give you a countdown messsage such as "press escape for boot menu"? Because if that is the case you need to edit the menu.lst file to change your boot menu countdown time. Unless you have the Grub 2 in which it is slightly different. What version of Ubuntu are you using?

---

### Post by mail.vipinaggarwal on 2010-03-09
no grub does not give any message. It just hangs after 'grub loading.'
I am using ubuntu 9.10
Grub 1.67 beta 4 is something that flashes on screen in booting process.

---

