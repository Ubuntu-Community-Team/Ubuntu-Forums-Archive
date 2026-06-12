---
title: "Safe to disable USB Legacy Support?"
date: 2009-10-25
forum: General Help
---

### Post by OrangeVixen on 2009-10-25
This is regarding a prior problem I got whenever booting after shuting down from Linux in which the boot would always freeze during the BIOS auto detecting USB mass storage devices.

So I did some searching and there was a mention about USB mass storage devices possibly being the problem and so, I disabled USB legacy support and it seems to have fixed the problem! Also makes boot faster now, but now I'm not sure if that will make other USB devices not work or what? I'm no USB expert, what problems might this fix bring up (for both Ubuntu and hardware)?

---

### Post by mgmiller on 2009-10-25
The single biggest problem I can think of is if you are using a USB keyboard.  With legacy USB turned off, you will not be able to use it get into your BIOS or to do anything in the grub menu.  This can be a big problem if you dual boot.  The keyboard will not work until after Ubuntu starts to do hardware detection (when the graphical boot screen starts its animation).  Same issue for USB mouse, but you don't usually need that till you're in the gui.

One workaround is to keep a cheap PS2 keyboard laying around for those rare occasions when you need to get into BIOS or grub.

Another work around for the mass storage devices is to power them off when you shut down and then wait till you are booted before powering them back up.  They should auto mount.  I would not want to leave an external drive turned on all the time anyway.

---

### Post by OrangeVixen on 2009-10-25
Oh yikes, well I guess I did that and discovered that my USB keyboard does work even with legacy off.

But here is the thing, I have no USB storage devices of any type connected, not before, during, or after I shutdown Linux, in fact, I never connected a single USB storage device since I got this computer.

I have a USB KB and Mouse, a USB printer that I have YET to connect, two SATA HDD, a floppy, an IDE CD/DVD RW... that's it. What else could be causing this?

---

### Post by mgmiller on 2009-10-25
The only other thing I can think of would be to go back into your BIOS and look carefully at the section that controls the boot order of devices.  Make sure only the connected drives are listed in the boot order.

BIOS's differ in how they do this, you may have to look at 2 different screens to determine what is selected for boot and then in what order they are called.

For example, you could list one of your optical drives, then your sata hard drive.  Don't give it a choice of USB anything or anything else.  Just those 2 devices.

Save the BIOS settings and try rebooting.

---

### Post by OrangeVixen on 2009-10-26
Oh, that got me on the right track!

I didn't realize my boot order included USB devices, but checking the boot order menu, there were a bunch of USB devices that were listed but don't actually exist. I think that might have caused the problem, I booted a couple of times and so far (knock on wood) it's not hanged yet.

I listed just my IDE CD/DVD and primary SATA HDD, I also turned off "Boot From Other Devices" (whatever that is).

I also renabled legacy USB support just to be safe, so far I think that fixed the problem.
Thanks you!

---

