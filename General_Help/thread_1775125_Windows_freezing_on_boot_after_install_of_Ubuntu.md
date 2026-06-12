---
title: "Windows freezing on boot after install of Ubuntu"
date: 2011-06-04
forum: General Help
---

### Post by MikeSz on 2011-06-04
Morning all,

A friend of mine has installed Ubuntu onto his system and now has a situation where it will no longer boot into Windows XP.

From what I can gather, he has downloaded the latest version, and run the installer from within windows.  He has two 320Gb drives and Ubuntu has installed itself on the second, leaving windows on the first hard drive.  It has also installed the grub menu.

When the unit is started, you can pick either linux or windows from the grub menu and it will boot into Ubuntu without any problems.  I have also looked at the hard drives from within Ubuntu and the first drive is still NTFS with all the windows directories on it.  

If you select windows from the grub menu, the Windows XP logo comes up though the system then simply freezes or re-boots itself.  Safe mode does not work either and it hangs with the last file being loaded showing as \WINDOWS\System32\DRIVERS\JGOGO.sys

The problem is he bought the machine second hand so doesnt have any of the recovery disks that came with the machine (though its a reasonably modern Pentium 4)

Does anyone have any ideas that doesnt need me to find a Windows XP disk and reinstall windows over the top of itself?

Many thanks!

---

### Post by MikeSz on 2011-06-06
Bump

---

### Post by MikeSz on 2011-06-07
Hi All,

does anyone have any ideas or is it going to just be a case of reinstalling windows over the top of itself and hoping for the best?

Many thanks,
Mike

---

### Post by misterbiskits on 2011-06-07
If it were my computer I would go into the bios, and set the computer to boot directly from my windows partition.  This would tell me whether or not windows is capable of booting on its own (bypassing grub).  That would narrow down the problem (ie windows is not broken)
Since your friend has xp on one drive and ubuntu on the other, you might be able to do this as well.

---

### Post by Mark Phelps on 2011-06-08
Having to guess here ... but if it was really installed while running Windows, then it was a Wubi install -- which creates a virtual filesystem on a Windows drive.  The result functions much the same as any other Ubuntu install, but it's contained entirely on a Windows drive.

If they can get into SAFE mode, they might try removing Ubuntu.  In Windows, that is treated like any other application -- so it should be removable.

But as to why Widows would freeze simply because of a Wubi install -- have no idea.  Sorry.

---

