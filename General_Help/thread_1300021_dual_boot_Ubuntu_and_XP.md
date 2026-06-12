---
title: "dual boot Ubuntu and XP"
date: 2009-10-24
forum: General Help
---

### Post by mrpeachy on 2009-10-24
I have 2 hdd's.
I used to have windows XP on both drives.
Installed XP on HD0 first then HD1

Then I installed Ubuntu on HD0 while I left HD1 alone.

Now I cant boot into XP on HD1
I get the message NTLDR is missing.

I put in the windows cd and booted from that to reinstall windows on HD1, it said that it needed to set up MBR on HD0 and that I should ceate a partition on my ubuntu drive for it. 

Is this possible or a good idea?

I have tried a few things that i have read like adding things to grub:
title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

but doesnt work.  I'm guessing that HD1 does not contain a windows MBR and that NTLDR is indeed missing.  If this is the case, how can I fix it?
Im thinking of maybe unplugging my ubuntu drive, installing xp again (so that installs thinking that HD1 is the primary drive) and then plugging HD0 back in, but would like to know if this would do any good first!

Thanks

---

### Post by Hugh Mulqueen on 2009-10-24
What are you trying to do?

Are you trying to: 
1. install ubuntu on hd0 and windows on hd1.
2. install windows _and_ ubuntu on hd0 and leave hd1 with a compatable filesystem for both OS's

Juging from your post i'd say you fecked up your windows install.

---

### Post by recluce on 2009-10-24
> **mrpeachy said:**
> I have 2 hdd's.

but doesnt work.  I'm guessing that HD1 does not contain a windows MBR and that NTLDR is indeed missing.  If this is the case, how can I fix it?
Im thinking of maybe unplugging my ubuntu drive, installing xp again (so that installs thinking that HD1 is the primary drive) and then plugging HD0 back in, but would like to know if this would do any good first!

Thanks

Copy the file "NTLDR" from a backup to the first partition of HD1 that is visible for Windows. You may need a few other Windows boot files too, if they are missing, like boot.ini. Make sure to set file attributes of NTLDR to read-only and hidden.

I am not sure that you need a new MBR on hd1. If so, start the repair console from an XP install disk.

---

### Post by mrpeachy on 2009-10-24
Thanks for the replies!

> **recluce said:**
> Copy the file "NTLDR" from a backup to the first partition of HD1 that is visible for Windows. You may need a few other Windows boot files too, if they are missing, like boot.ini. Make sure to set file attributes of NTLDR to read-only and hidden.

I am not sure that you need a new MBR on hd1. If so, start the repair console from an XP install disk.

HD1 is a single partition, so NTLDR would go alongside my WINDOWS, WINNT etc folders and not in them?

---

### Post by Hugh Mulqueen on 2009-10-24
The NTDLR is a file in your windows filesystem. the name of the standard windows filesystem is called ntfs.
A MBR or Master Boot Record is on each hard disk. Windows installed its self on both hard disks. When you installed ubuntu it installed its self on the MBR.

I still dont understand what your trying to do.

Either you had 2 installs of windows on seperate partitions or hdds.
or you had windows on one partition and just formated the other one with ntfs.

---

### Post by gibpyx on 2009-10-24
I used this guide

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by mrpeachy on 2009-10-24
I fixed this myself.
unplugged ubuntu HDD power and IDE cables
reconnected XP HDD so that computer recognized it as primary drive

ran XP install disk and repaired the windows installation.

set everything back up to the way it was, ubuntu HDD as primary, XP HDD as secondary then went with adding:

title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

to grub menu.lst

works!

---

