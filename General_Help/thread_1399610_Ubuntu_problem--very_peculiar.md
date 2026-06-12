---
title: "Ubuntu problem--very peculiar"
date: 2010-02-05
forum: General Help
---

### Post by Gandalf_the_Grey on 2010-02-05
Prior to upgrading my motherboard, Ubuntu 9.10 functioned perfectly.  Now that I've upgraded, however, Ubuntu no longer works, and I can't get it to reinstall.  If I try "Try Ubuntu without changing your computer", it freezes at the flashing logo.  In verbose mode (deleting the "quiet" argument), it halts at either "Loading, please wait..." or right after a message about putting the kernel text in read-only mode.  The same thing happens if I use the "Install Ubuntu" mode instead.  In the Alternate CD, the results are completely random.  It either freezes at a flashing cursor with nothing else displayed, or it freezes at random points in the start-up procedure.  I've verified that the disks are OK by booting another computer just fine with them.

My hardware:
Asus P4R800-VM motherboard
Pentium 4 3 GHz CPU
1 GB RAM
ATI Radeon 9100 IGP

---

### Post by switch10 on 2010-02-05
I would check the RAM with the liveCD.  

How many beeps are you getting when you turn the system on?  One beep is usually normal.  Any more than that look in your Motherboard manual.

---

### Post by dcstar on 2010-02-06
> **Gandalf_the_Grey said:**
> Prior to upgrading my motherboard, Ubuntu 9.10 functioned perfectly.  Now that I've upgraded, however, Ubuntu no longer works, and I can't get it to reinstall.  If I try "Try Ubuntu without changing your computer", it freezes at the flashing logo.  In verbose mode (deleting the "quiet" argument), it halts at either "Loading, please wait..." or right after a message about putting the kernel text in read-only mode.  The same thing happens if I use the "Install Ubuntu" mode instead.  In the Alternate CD, the results are completely random.  It either freezes at a flashing cursor with nothing else displayed, or it freezes at random points in the start-up procedure.  I've verified that the disks are OK by booting another computer just fine with them.

My hardware:
Asus P4R800-VM motherboard
Pentium 4 3 GHz CPU
1 GB RAM
ATI Radeon 9100 IGP

Try the basic video mode option on the install CD.

---

### Post by Gandalf_the_Grey on 2010-02-06
I have already tested my RAM.  Also, Fedora 10 functions just fine on this machine.  My computer gives two quick beeps on startup, however, this seems to change depending on whether I have any USB devices plugged in at the moment.  I will try the video mode next.

---

### Post by Gandalf_the_Grey on 2010-02-06
No, changing the video mode did nothing.  It froze at a flashing cursor if I left "quiet" and "splash" on, or it froze at "Loading, please wait..." if I turned those options off.

---

### Post by Gandalf_the_Grey on 2010-02-08
OK, turns out it was one of those "Duh" issues.  My BIOS was version 1002.  The latest is 1007.  Flashing the BIOS to 1007 caused Ubuntu to function perfectly.

---

### Post by Iowan on 2010-02-08
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

