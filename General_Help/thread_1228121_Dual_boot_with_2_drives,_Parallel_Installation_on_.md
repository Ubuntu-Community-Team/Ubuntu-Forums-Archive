---
title: "Dual boot with 2 drives, Parallel Installation on Windows drive"
date: 2009-07-31
forum: General Help
---

### Post by Michl on 2009-07-31
I dual boot with Windows 2000 on slave and Hardy on the master.
I just read on 'support.microsoft' that I can
"Install Windows XP to a new folder (parallel installation)"

Has anyone done this?  Will the Windows set-up erase the
Linux grub file?  What should I worry about?

---

### Post by Michl on 2009-07-31
This is no problem.

On a laptop set-up to dual boot (but on one
drive) to Windows 2000 and Intrepid, I installed
Windows XP to the NTFS partition, leaving the
file system intact.  The install CD installs
XP to /windows and leaves 2000 in /WNNT.  You
can then load either of the 2 operating systems,
but grub is gone.

To reinstall grub, go to HOWtoinstall grub on
the wiki ubuntu site and follow the directions.
Once grub is installed, when you load the other
operating system, you get the windows loader
menu with 2000 and XP on it.  All three systems
load without a hitch.

So I am confident that the same will hold with
a 2 drive dual boot system.

---

