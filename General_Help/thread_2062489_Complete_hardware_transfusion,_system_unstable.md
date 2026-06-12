---
title: "Complete hardware transfusion, system unstable"
date: 2012-09-25
forum: General Help
---

### Post by SanDiegoSeahawk on 2012-09-25
Hello,

I recently did a complete hardware transfusion of my Ubuntu AMD64 12.04 system.  I literally replaced all of the following components of my system:
-Motherboard
-CPU
-Power Supply
-System Disk
-Memory
-Video Card

I cloned the old boot drive, which was IDE, to a new SATA drive.  I upgraded the CPU from an AMD II Phenom x6 to a an AMD FX-8120.  The motherboard is now an ASUS Sabertooth 990FX.  I went from DDR2 to DDR3 memory.

The system booted and for the most part seems okay.  I do see some random instability that I'd like to try to figure out.  On occasion, an App will freeze and it's window will dim, sometimes for up to 10-20 seconds or more.  Applications that I recall be rock solid now crash occasionally.  Chrome crashes consistently if I try to open the bookmark manager. 

I've run a memtest and that passed fine.  I've also run Smart tests on my system disk and it passes.

From what I've read, I should be able replace this hardware like this and Ubuntu should handle the changes.

Any thoughts on what to investigate?  Is it unreasonable to expect the system to be stable after changing out this much hardware?

---

### Post by TenPlus1 on 2012-09-25
Ubuntu should be able to handle booting into a new system and using the new hardware without a problem although I would uninstall and reinstall the video drivers to be sure of compatibility...

Cloning is indeed a good backup technique but if it were myself, I'd be eager to have a fresh 12.04-1 install on such a new setup with '/' and '/home' partitions set independantly...

---

