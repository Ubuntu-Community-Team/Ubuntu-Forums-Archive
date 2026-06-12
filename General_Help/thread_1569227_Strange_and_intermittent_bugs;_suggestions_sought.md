---
title: "Strange and intermittent bugs; suggestions sought"
date: 2010-09-06
forum: General Help
---

### Post by quadproc on 2010-09-06
In the last few days, this computer has experienced strange and intermittent problems.  I hope that you guys can suggest what might be causing the problems and, if you have seen such problems before then please tell me anything you can about them.

This computer has run fairly reliably since it was new a year ago.  But a couple of days ago I experienced this:

Problem #1: I had turned the system on and used it for a while, then left it idling for a couple of hours.  It had been working normally.  When I went back to it, I started to respond to an email but while I composed my reply, the system suddenly stopped taking keyboard input and sent the incomplete reply.  Then, although I could move the cursor as usual, any place where I clicked the left mouse button I received an irrelevant window of selections, as though the cursor was pointing to some other place (always the same selections).  I could not access the shutdown menu so I pressed the RESET button on the computer.  The reboot seemed to occur normally and I logged back in, but the same problem of the cursor not knowing where it was located was still present!  Remember, this was after a hardware reset and reboot, although power had remained on.  I turned off the power to the computer and left it for a while, then when I repowered it I started memtest86 which ran about 2/3 of its pass without errors before I hit ESC and rebooted into Ubuntu.  It ran normally after that.

Problem #2:  A day later, I turned the system on and booted memtest86.  The memory test ran without errors for about 1.5 passes after that cold start so I rebooted the system into normal operating mode.  It ran OK for a few minutes but then it stopped taking keyboard input.  I could move the cursor with the mouse but keystrokes were ignored.  I fired up another computer and used ssh to connect to the problem machine; that connection worked and I was able to use the problem machine through ssh, but the problem machine remained oblivious to its keyboard input.  So, through ssh, I executed a "shutdown now" command.  The second computer reported that the connection was terminated (good), but the problem computer was still running except that now it was ignoring mouse inputs as well so the cursor could not be moved.  But the normal screen display was still present.  This situation persisted for several minutes until I pressed the reset button; that did its usual function and the system behaved normally thereafter.

Some information regarding the problem system:

ASUS P6T SE motherboard
Intel 950 CPU, no overclocking
6 GB RAM
HD4870x2 graphics cards
3 WD Caviar disks, SATA
850 watt power supply running at 40% capacity
HAF case
Ubuntu 9.10 64 bit
fglrx v10.3 graphics driver

Any ideas, experience with something similar, insights, or anything else useful?  Thanks.

quadproc

---

