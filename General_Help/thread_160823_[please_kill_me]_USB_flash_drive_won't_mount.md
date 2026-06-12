---
title: "[please kill me] USB flash drive won't mount"
date: 2006-04-15
forum: General Help
---

### Post by ChrisC on 2006-04-15
I can't my USB flash drive to mount.  It's actually a MemoryStick from a digital camera, and has automounted plenty of times before.  Just not this time :(

Here's what I already know / have tried:
 - rebooted system (not with drive plugged in)
 - dmesg shows nothing upon plugging in
 - hal is running
 - there is no /dev/sd* (it's usually sda I think)
 - lsusb shows the card reader on bus 3 device 2

Help?

---

### Post by ChrisC on 2006-04-16
I rebooted the machine WITH the flash drive plugged in, and it showed up properly on my desktop after it booted and logged me in.  Unmounted, removed, reinserted, and it automounted properly.

This has hit me before.  What's going on here?  Vanilla Breezy system.

---

### Post by jinacio on 2006-04-16
did you do an update by any chance? 
anyway, guess i can't be of much help now... unless you need someone to kill you? :P

---

### Post by zeroconf on 2006-04-16
I updated on 15th of April 2006 my Edubuntu 5.10 system. I mentioned, that kernel 2.6.12 were installed. After that USB just doesn't work. Plug or not - nothing happens. lsusb and proc doesn't show anything... Actually this was clean install of Edubuntu 5.10. Then I just made also updates due to system tray announcement.
I just were happy, that Ubuntu and its derivates are the best Linux distros due to excellent USB support. But now it seems like not stable.... I'm really sad of this...

---

