---
title: "Blue Screen of death after using 9.10 from USB stick"
date: 2010-03-21
forum: General Help
---

### Post by DrScum on 2010-03-21
I created a USB stick with Ubuntu 9.10, used it to boot a dell Inspiron 1550 laptop which has WinXP. I tested 9.10, everything went fine out of the box so to speak. But when I went back and tried to boot XP again I got a blue screen. XP starts in safe mode and no apparent problems are detectable but it will not start in Win normal mode anymore.

Does anyone have any ideas?

---

### Post by quixote on 2010-03-23
I'm out of my depth, but maybe if you tried to run scandisk or chkdisk it would give you some useful info or do something helpful? ??

The most common problem is that an OS clobbers the master boot record, and then nothing else will boot, but that doesn't seem to be your problem because WinXP does boot.  It's almost as if some flags have been set or something which XP doesn't understand.

---

### Post by Megafag on 2010-03-23
> **DrScum said:**
> I created a USB stick with Ubuntu 9.10, used it to boot a dell Inspiron 1550 laptop which has WinXP. I tested 9.10, everything went fine out of the box so to speak. But when I went back and tried to boot XP again I got a blue screen. XP starts in safe mode and no apparent problems are detectable but it will not start in Win normal mode anymore.

Does anyone have any ideas?

So you are saying you booted into a livedisk, did nothing to your windows partition, and now its bluescreening?

---

### Post by dcstar on 2010-03-23
> **DrScum said:**
> I created a USB stick with Ubuntu 9.10, used it to boot a dell Inspiron 1550 laptop which has WinXP. I tested 9.10, everything went fine out of the box so to speak. But when I went back and tried to boot XP again I got a blue screen. XP starts in safe mode and no apparent problems are detectable but it will not start in Win normal mode anymore.

Does anyone have any ideas?

Power off the machine, take the battery out to totally reset the hardware and then put it back together and see what happens.

---

### Post by PRC09 on 2010-03-23
Did you change the bios to boot from usb??? If so what else do you have plugged into usb when you boot.I have one system that will not boot when my Ipod is plugged in......Set  boot back to normal and all is fine....

---

### Post by DrScum on 2010-03-23
Yes, I did boot from a live USB stick, used some programs, got connected to the internet using the W-Lan connection but didn't do anything to the partition or the hardware configuration other than changing the boot sequence in order to be able to boot from the usb stick. 
I did follow the various suggestions, including changing the boot sequence back to the original, and still have the problem. XP doesn't boot in normal mode, it does boot in save mode though. When I boot there is nothing plugged into the usb port.

---

### Post by JKyleOKC on 2010-03-23
> **DrScum said:**
> When I boot there is nothing plugged into the usb port.Try booting with the live USB stick plugged in, but the boot sequence back to normal. It's possible that the normal Win boot code is looking for something at the USB port and throwing an error when it fails to find it; the safe mode boot skips most of the drivers and thus can get around whatever is going on.

It's also possible that something created a "flag file" that's forcing Windows into safe mode; if this is the case, though, such a file should be cleared out automatically after the first safe-mode boot. That's why I suggest trying with the same stick in the USB port, so if it's trying to look there it will be able to find what it's looking for...

---

### Post by DrScum on 2010-03-24
I tried what JKyleOKC suggested to no avail. 
Ultimately I ended up using the system recovery option of the safe mode and restored a system config safed a couple weeks ago. I didn't loose anything of great importance as far as I can tell now. 

However, the whole issue leaves me kind of scared I'd prefer to know what really happened.

---

### Post by quixote on 2010-03-24
One thing you could try, if you're feeling brave and energetic and now that you have a way of fixing it, is to go through the same steps that you think caused the problem to begin with.  Set a recover point in Windows first, and then try the exact same steps and see if it forces Win into safe mode booting again.  If yes, it had something to do with the USB.  If no, maybe it was just some Windows thing, unrelated to anything you did.

---

