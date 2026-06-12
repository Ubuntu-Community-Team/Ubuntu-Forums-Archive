---
title: "Dual booting with windows 7 and linux netbook remix. Checkdisk problem"
date: 2009-12-21
forum: General Help
---

### Post by FEnzo on 2009-12-21
I just installed linux netbook remix on a new partition on my windows 7 installed hp tx2z.
and now everytime after i run the linux and trying to restart the windows, win7 tells me it has to check my disk C which is my only disk before it starts up. it says i can cancel the check by pressing any button within 10 secs, but my keyboard won't work, and after the 10sec counter down, the computer just freezes. it happens everytime.
any ideas?
THanks!

---

### Post by Mark Phelps on 2009-12-21
Can't provide specifics without some details first ...

How did you install Ubuntu? Inside Win7 (using Wubi) or in its own partitions?

If the second, how did you shrink the Win7 partition to make room? Did you do it (the right way) using Win7 Disk Management utility? OR did you do it (the risky way) using the Ubuntu installer to shrink the OS partition?

IF you did the last, you will need to find a way to boot into the Win7 command line and run chkdsk from there.  Don't know how your particular machine is setup, but that's generally done pressing F8 as soon as you enter your password -- which will provide a text screen allowing you to select the option to boot into a command line.

---

