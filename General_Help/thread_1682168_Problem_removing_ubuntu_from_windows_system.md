---
title: "Problem removing ubuntu from windows system"
date: 2011-02-05
forum: General Help
---

### Post by dave clark on 2011-02-05
I am running a Windows XP sp3 system and some time ago wanted to try out Ubuntu Linux. I ordered a disk containing Ubuntu 9.10 and installed Linux. The disk created a new partition on my 
machine for Linux and (somewhere) set up a utility called Grub which provided dual boot options to go into either operating system with Linux the default.

I have looked over Linux now for a couple of years and while I like speed, security and stability, I cannot use most of the software that I gained expertise in over the years.

I decided to remove Linux from my system as I was using it less and less. I obviously made the mistake of assuming that I could simply remove the partition that the Ubuntu disk had created and with it gone, my machine would revert to starting up in Windows XP.

I now have no access to my computer. On startup, the Grub utility is still activated and I get the following message and the system hangs:

Grub Loading
error: no such partition
grub rescue>_

Obviously, the Grub utility is still somewhere in the startup sequence of my windows partition, but I don't know what it is or where it is. Further, I don't know how to get into my windows 
system now to look for it as it hangs after the grub error report.

Can anyone help me? 

Worst case, I do have a full backup that I could use to restore my system, but it is a month old and I would lose some important data. It would also reinstall linux which defeats my effort to 
remove it and free up space on my hardrive.

Many thanks
Dave Clark

---

### Post by GOROSSI on 2011-02-05
have you tried fixmbr from your xp disc?? 

That most likely the fix

---

