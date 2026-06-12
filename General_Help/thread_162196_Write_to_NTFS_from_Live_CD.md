---
title: "Write to NTFS from Live CD?"
date: 2006-04-18
forum: General Help
---

### Post by OMRebel on 2006-04-18
Have a bit of a problem.  A buddy has a XP laptop, but a dll is seriously screwed up (HAL.DLL).  I can't run the Repair off the XP CD because he doesn't know what his Administrator password is.  I have copied the dll to a jump drive, and booted his laptop up off of the Breezy Live CD.  Is it safe to write this dll to his /windows/system32 directory?  His file system is NTFS.  Or, would this really screw up his computer?  If it will mess it up, how can I find his Administrator password?

---

### Post by aysiu on 2006-04-18
Since the computer's screwed up already, you should use the Ubuntu live CD to save the important data and then you can *try* using something like NTFS-Fuse to write to Windows. Otherwise, reinstall after you save the data.

---

### Post by Fysidiko on 2006-04-18
I'd give Knoppix Security Tools a go ( [http://s-t-d.org/](http://s-t-d.org/) ) - it can recover the adminstrator password for you, after that you can use the recovery console. Otherwise, I agree with aysiu.

---

### Post by Computeruser on 2006-04-18
I agree on the Knoppix security tools, but what I keep around is a BartPE live CD. This is an XP live CD that you make yourself. You can load Cain and Abel on that and Cain can fish out the administrator password in a few seconds. Plus BartPE is NTFS and can talk to the NTFS system without problem.  Good luck.

---

