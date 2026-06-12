---
title: "Win7 freezes after using Linux"
date: 2012-05-28
forum: General Help
---

### Post by Ryupower on 2012-05-28
I've been having a problem, windows 7 always freezes after using an installed linux. I've searched the internet to no avail (always get back to an unanswered thread regarding someone after booting into LiveCD). It doesn't matter if it's Ubuntu, debian, SuSE, what have you.


And no, Chkdsk/r does NOT help...
The problem is usually 'resolved' when I log in to Windows 7 safe mode for more than 6 minutes, and 'explore' my files or just leave it to sit and do nothing until reboot. Whenever I reboot THEN (and only if it's into windows 7) it has a high chance in functioning again...until I use linux again. There has to be an easier way than this. Chksdsk-ing the windows partition on boot-up makes no difference whatsoever, so I really don't know what's up.

Some info:
ASUS
MBR enabled (do I have to disable it?)
Partitions on two different hard drives.

Thanks!

---

### Post by Jerry N on 2012-05-28
I have something similar on two computers using Gigabyte motherboards.  If I have used linux and reboot to Win 7, the ethernet adapter does not work.  If I have used Win 7 and reboot to linux, the ethernet adapter does not work.  My solution:  Turn off the computer power _completely_ when changing from linux to Win 7 and vice-versa.  Just powering down the computer doesn't work, the power must be removed.  

You might see if this works for your problem.

Jerry

---

### Post by Mark Phelps on 2012-05-29
You said you have two drives.  I'm hoping that you have them set up so that each "OS" is on its own drive -- and each drive is bootable by itself.

That would mean that the Win7 drive would NOT have GRUB installed to it.

I've seen reports of cases where, if GRUB is installed to the Win7 drive, that presents problems to Win7 in booting.

If your drives are independently bootable, suggest you try booting into and outof Win7 a few times with only that drive connected.  That should work without problems.

If that works OK, then try booting into and outof the Ubuntu drive, with only it connected.  If that works OK, then open a terminal and enter "sudo update-grub".  This will rewrite your GRUB config file.  Then, reboot.

Once that is done, reconnect your Win7 drive -- but this is important -- continue to boot from the Ubuntu drive.  Once you boot into Ubuntu, enter the same command again.  That will rewrite your GRUB config file again.

Then, see if you still have the old problem booting into and outof the OSs.

---

