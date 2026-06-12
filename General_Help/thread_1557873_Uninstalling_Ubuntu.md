---
title: "Uninstalling Ubuntu"
date: 2010-08-21
forum: General Help
---

### Post by Badger Meat on 2010-08-21
I was previously on Windows 7 and then had to get a new hard drive as my old one died on me.  As I had a Ubuntu disc lying around, I decided to install it onto this computer, but honestly, I can't stand the OS and can't do anything that I'm used to doing (and doing it slower when in Linux).  My question is, how do I completely reformat this hard drive / how do I install WIndows onto this computer, when my BIOS isn't letting me edit it.  The Windows disc doesn't try to load, no matter what I try to do to it.

---

### Post by howefield on 2010-08-21
Boot with the Ubuntu disk to the desktop in Live mode. Then use GParted (System > Administration > GParted) to format the drive to ntfs. Then  try with your Windows disk.

As always, make sure you have backed up any valuable data before doing anything destructive to the disk, if you have any.

---

### Post by corrytonapple on 2010-08-21
What version of Ubuntu? What are you doing with it? What are your system specs? See this:
[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

---

### Post by Mark Phelps on 2010-08-21
> **Badger Meat said:**
> I was previously on Windows 7 and then had to get a new hard drive as my old one died on me.  As I had a Ubuntu disc lying around, I decided to install it onto this computer, but honestly, I can't stand the OS and can't do anything that I'm used to doing (and doing it slower when in Linux).  My question is, how do I completely reformat this hard drive / how do I install WIndows onto this computer, when my BIOS isn't letting me edit it.  The Windows disc doesn't try to load, no matter what I try to do to it.

You're not uninstalling Ubuntu; you're wiping the drive and installing Win7.

You will have to be able to get into your BIOS to set it to boot from the DVD drive -- or you won't be able to do anything else.

The documentation that came with your PC will tell you what key to press to boot into the BIOS.  Typical such keys include Esc, Del, F11 -- but the key is specific to your make and model machine.

---

### Post by Badger Meat on 2010-08-21
Can't load from the disc without accessing my BIOS. I've tried all possible keyboard commands to load it up, but it's not listening to me.

---

### Post by corrytonapple on 2010-08-21
Computers don't listen, they respond. Did you set BIOS password protection?

---

### Post by ajgreeny on 2010-08-21
How did you manage to install Ubuntu in the first place if you can't get into the bios?  The machine may be set already to boot to the CD, but I think that windows CDs will sometimes not boot at all if there is no available hard disk to install to;  having ubuntu on the hard disk means that windows thinks there is no disk, because it is not clever enough to see the ubuntu install.

So you need to boot to the ubuntu live CD and use gparted in the System->Administration menu to delete your ubuntu partitions and either leave unallocated space or make a new ntfs partition, exactly as howefield said.

If you can not boot to the ubuntu CD, I can't really help more, other than to say that you will have to keep trying various keys at switch-on until you get to the bios screen.  Normally there is a message that flashes onto the screen after you hit the power button, saying "Press Del (or some other key or combination) to enter setup".  Look closely and you may find something you did not even know was there.

---

### Post by xircon on 2010-08-21
Are you using a USB keyboard? Try a PS/2 keyboard.

---

