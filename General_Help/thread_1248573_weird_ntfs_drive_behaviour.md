---
title: "weird ntfs drive behaviour"
date: 2009-08-24
forum: General Help
---

### Post by hammeraxe on 2009-08-24
My setup: Lenovo IBM T60 running Windows XP from its internal 70 GB hard drive + Ubuntu 9.04 Wubi install on an external 1,5TB drive.

The problem: The setup always worked fine. At one point, though, windows crashed and I had to restart. It could not boot up again showing UNMOUNTABLE_BOOT_VOLUME error. 
*Safe mode does not work, recovery partition does not work. 
*Ubuntu sees the disk and can read/write without problem. 
*ntfsfix says the filesystem is corrupt
*Windows recovery CD cannot find the hard drive

All the solutions on the net regarding this error suggest using the recovery cd and performing a ckhdsk, mbrfix and what not. This is impossible, as the disk seems to have vanished in the windows universe.
Any suggestions on how to fix this, preferably without sweeping the entire disk?

---

### Post by cascade9 on 2009-08-24
I would bet your NTFS drive is 'dirty'. ntfsfix may fix it. 

[http://manpages.ubuntu.com/manpages/karmic/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/ntfsfix.8.html)

---

### Post by jbeukema on 2009-08-24
Have you tried reinstalling the MBR and/or bootsector?

try fixboot and fixmbr from the windows/dos recovery console

---

### Post by P4man on 2009-08-24
so if you boot a windows cd in recovery mode, with the wubi/ubuntu drive disconnected, its not finding any disk at all?

In that case there is something seriously wrong with it. If ubuntu can somehow (Id say magically lol) read the drive, take advantage of it to make a backup before doing anything else. Then you can try testdisk on ubuntu to see if it can salvage the drive. It does sound like an MBR issue.

---

### Post by hammeraxe on 2009-08-24
> so if you boot a windows cd in recovery mode, with the wubi/ubuntu drive disconnected, its not finding any disk at all?

This is exactly the case. Backup was the first thing I did when I logged on Ubuntu.

> I would bet your NTFS drive is 'dirty'. ntfsfix may fix it. 

Actually I already tried ntfsfix once, but now I looked at it once more and an epiphany came upon me: I had used it with /dev/sda rather than /dev/sda1. So now it worked and Windows runs CHKDSK at this very moment. I am getting a whole lot of output. Hopefully this will end good.

---

### Post by jbeukema on 2009-08-24
> **hammeraxe said:**
> This is exactly the case. Backup was the first thing I did when I logged on Ubuntu.



Actually I already tried ntfsfix once, but now I looked at it once more and an epiphany came upon me: I had used it with /dev/sda rather than /dev/sda1. So now it worked and Windows runs CHKDSK at this very moment. I am getting a whole lot of output. Hopefully this will end good.

Does your drive support S.M.A.R.T. monitoring?

---

### Post by hammeraxe on 2009-08-24
Ok, CHKDSK finished and I am writing this from Windows XP, which now works like a charm :/ Yet I am not sure how stable the system will be in the long run.

> **jbeukema said:**
> Have you tried reinstalling the MBR and/or bootsector?

try fixboot and fixmbr from the windows/dos recovery console

Is there any point in doing this now that the drive works miraculously?

> **jbeukema said:**
> Does your drive support S.M.A.R.T. monitoring?

I have no idea. How do I check this?

---

### Post by cascade9 on 2009-08-24
> **hammeraxe said:**
> Actually I already tried ntfsfix once, but now I looked at it once more and an epiphany came upon me: I had used it with /dev/sda rather than /dev/sda1. So now it worked and Windows runs CHKDSK at this very moment. I am getting a whole lot of output. Hopefully this will end good.

Phew! It was either a dirty NTFS or a dead drive. You may want to take hammeraxe's advice, SMART doesnt take much system resources these days,.

> **hammeraxe said:**
> Ok, CHKDSK finished and I am writing this from Windows XP, which now works like a charm :/ Yet I am not sure how stable the system will be in the long run.

Is there any point in doing this now that the drive works miraculously?

I have no idea. How do I check this?

Nope, no real piont in running fixmbr/etc. The only point of doing that was to fix winXP, which is now working agian. It should be fine, I've had dirty NTFS problems before and the OS kept running for years (literally)

SMART is more of a BIOS setting, Hdds have suported SMART for a long, long time. Enable it in BIOS.

---

### Post by jbeukema on 2009-08-24
> **hammeraxe said:**
> 


Is there any point in doing this now that the drive works miraculously?


NO!!!!!!!!


> I have no idea. How do I check this?

It might say on the drive itself or you can check the model number (from Device Manager) against the manufacterer's website and see whether they have a SMART monioring program for download. Generic SMART readers are out there, but I don't know whether they're to be trusted.

---

### Post by P4man on 2009-08-24
You can check in the bios, there is usually something that allows you to enable smart monitoring. If its enabled, you can use a program such as:
[http://www.ntfs.com/disk-monitor.htm](http://www.ntfs.com/disk-monitor.htm) (for windows) to monitor the harddisk health. For linux you'd use smartmon (its in the repo's).

That said, SMART is well.. not all that useful. Havent ever seen it catch a problem before it was too late. If you suspect your disk is dying, try a real diagnostics program.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Its a bootable cd that contains diagnostics programs for every possible vendor.

---

### Post by jbeukema on 2009-08-24
a TRUE test would be a read/wtrite test, but such tests are destructive. You'll be limited to read-only if you wish to preserve your data

---

### Post by cascade9 on 2009-08-24
> **P4man said:**
> That said, SMART is well.. not all that useful. Havent ever seen it catch a problem before it was too late. If you suspect your disk is dying, try a real diagnostics program.

SMART has worked for me, but I knew that hdd had problems before SMART told me. Sounded like someone had put a 2 plates and a load of ball bearings into a tin can and was shaking it the whole time the PC was on.

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> a TRUE test would be a read/wtrite test, but such tests are destructive. You'll be limited to read-only if you wish to preserve your data

Why ? You can read each byte or sector, keep the contents in memory,  do a read/write test, and then put the original data back there. Im not 100% sure if thats what those diagnostics programs do, but Id hope so!

---

### Post by jbeukema on 2009-08-24
> **P4man said:**
> Why ? You can read each byte or sector, keep the contents in memory,  do a read/write test, and then put the original data back there. Im not 100% sure if thats what those diagnostics programs do, but Id hope so!

I've never heard of one that does that, but on might exist.

---

### Post by hammeraxe on 2009-08-24
> **cascade9 said:**
> SMART has worked for me, but I knew that hdd had problems before SMART told me. Sounded like someone had put a 2 plates and a load of ball bearings into a tin can and was shaking it the whole time the PC was on.

Brrr... I remember my dad's Samsumg laptop slowly dying with that sound. As if it had swallowed a knife and would be cutting itself apart from the inside.

> **P4man said:**
> You can check in the bios, there is usually something that allows you to enable smart monitoring. If its enabled, you can use a program such as:
[http://www.ntfs.com/disk-monitor.htm](http://www.ntfs.com/disk-monitor.htm) (for windows) to monitor the harddisk health. For linux you'd use smartmon (its in the repo's).

That said, SMART is well.. not all that useful. Havent ever seen it catch a problem before it was too late. If you suspect your disk is dying, try a real diagnostics program.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Its a bootable cd that contains diagnostics programs for every possible vendor.

I'll have a look at these. It would be nice if there actually was a reliable way of keeping your hard disks alive, though.

---

### Post by cascade9 on 2009-08-24
A good start is cooling IMO. I am yet to have any of my fan and/or heatsink cooled Hdds die *crosses fingers*.

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> I've never heard of one that does that, but on might exist.

If my own memory isnt corrupt, i seem to remember running both seagate and maxtor diagnostics which did a write test, and it wasnt destructive.

---

