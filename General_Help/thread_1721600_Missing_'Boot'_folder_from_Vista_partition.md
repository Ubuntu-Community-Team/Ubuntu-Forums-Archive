---
title: "Missing 'Boot' folder from Vista partition"
date: 2011-04-04
forum: General Help
---

### Post by rudipoo on 2011-04-04
Hi,

I have been foolish and accidentally deleted the 'Boot' folder from my Vista partition and now cannot boot Windows from the GRUB launcher. I'm not sure what to do next, since I can't find the recovery DVD either.

I managed to find a site with the 'bootmgr' file available to download but couldn't find anywhere to download the contents of the 'Boot' folder. Can anyone point me in the right direction? Is there any software that can be run in Ubuntu (which launches perfectly well of course) which might fix this?

Thanks

---

### Post by oldfred on 2011-04-04
Download this. Then copy bootmgr & /boot/BCD over. You then use it to repair your boot. Not sure what else you may have deleted.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You may get better help in a windows forum.

---

### Post by rudipoo on 2011-04-05
Thanks very much that worked perfectly: I made the disc and booted it on restart, then on one of the first screens clicked 'repair' and it worked again within seconds!

Cheers

---

