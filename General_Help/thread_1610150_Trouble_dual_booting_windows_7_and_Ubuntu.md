---
title: "Trouble dual booting windows 7 and Ubuntu"
date: 2010-10-31
forum: General Help
---

### Post by Jynxx on 2010-10-31
Hello all. I'm  having some trouble dual booting windows 7 and ubuntu. A clean install of windows 7 creates a 100MB system reserve partition as the first partition on the HDD. When I go to install Ubuntu on a third partition, Grub isn't allowing me to boot windows 7. I'm not sure if Grub is seeing partition 1 as the root or what. Has anyone dealt with this and does anyone have a solution for this? I can mount the windows disk in Ubuntu but can't boot into windows.

---

### Post by Quackers on 2010-10-31
Is the grub menu appearing or is it just booting straight into grub?

---

### Post by Jynxx on 2010-10-31
> **Quackers said:**
> Is the grub menu appearing or is it just booting straight into grub?

The Grub menu does appear and it shows windows but what I believe its showing is that first system reserve partition. Since there is no OS on that partition, it won't boot into windows.

---

### Post by Mark Phelps on 2010-10-31
No, that first partition is not necessarily your problem.  It contains the Win7 boot loader, not the OS.  The second partition most likely your Win7 OS partition -- containing the OS, programs, and your other files.

In some cases, GRUB gets confused and creates two Win7 entries -- so try them both (if you have two).  Use the one that works from now on -- even if it is the second entry.

Did you shrink the Win7 OS partition using the Ubuntu installer in a side-by-side installation? Or did you shrink the Win7 OS partition using the Win7 Disk Management utility -- the right way.

IF you did the first, Win7 won't boot until you repair it because allowing the Ubuntu installer to shrink the OS sometimes results in a corrupted partition.

When you were in Win7, you SHOULD have used the Backup feature to create and burn a Win7 Repair CD.  But since you probably did not do that, go to the appropriate link below, download and burn a Win7 Repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from that CD and run  Startup Repair three times -- that's right, three times.  That should get you booting back into Win7 OK.

You will then have to reinstall GRUB from the Ubuntu CD.

---

