---
title: "Win7 won't boost after Ubuntu install"
date: 2010-09-27
forum: General Help
---

### Post by kfriddile on 2010-09-27
After installing Ubuntu I get the following error when selecting Windows 7 from the grub menu:

> Windows failed to start. A Recent hardware or software change might be the cause. To fix the problem: 

1. Insert your windows installation disc and restart your computer.
2. Choose your langugae settings, and then click next
3. Click "repair your computer."

Status: 0xc000000e
Info: The boot selection failed because a required device is inaccessible.

My machine has two disks (sda and sdb).  Windows was installed on sda first, and then Ubuntu was installed on sdb.  GParted shows sda as having the 100MB reserved NTFS partition that Win7 automatically creates, but the rest of the disk is shown as "unallocated" even though it should be an NTFS partition.  I tried the automated repair utility on the Win7 disk, but it had no effect.  Please help, this is urgent.

---

### Post by pqwoerituytrueiwoq on 2010-09-27
unplug the ubuntu HD and see windows will boot off the other HDD
just to make sure it is there
if it is there windows is porbally looking for the install on the ubuntu disk in which case boot.ini will need editing (win7 still uses that file right?)

---

### Post by marin123 on 2010-09-27
did win 7 work when you installed it? or maybe you marked it for formatting when you were installing ubuntu?

---

### Post by kfriddile on 2010-09-27
> **pqwoerituytrueiwoq said:**
> unplug the ubuntu HD and see windows will boot off the other HDD
just to make sure it is there
if it is there windows is porbally looking for the install on the ubuntu disk in which case boot.ini will need editing (win7 still uses that file right?)

Both disks are definitely present and recognized.  GParted sees them both, and the error message I'm given is a Windows-specific error that would be impossible to see if the Windows disk simply didn't work.  Besides, this is a laptop, so pulling out individual components isn't as trivial as with a desktop machine.

---

### Post by kfriddile on 2010-09-27
> **marin123 said:**
> did win 7 work when you installed it? or maybe you marked it for formatting when you were installing ubuntu?

Yes, it worked.  I'm positive I didn't somehow mark it for formatting.  Besides, if it had somehow been formatted, it wouldn't show as "unallocated" would it?

---

### Post by PabloTempe on 2010-09-27
It may be time to go into the Windows HD with Ubuntu, back up all the files you need to keep and then reinstall everything. You can waste hours/days trying to diagnose/fix a bad install that may well be unfixable. Trust me, I've done it and I still had to reinstall anyway.

Pablo

---

### Post by marin123 on 2010-09-28
> **kfriddile said:**
> Yes, it worked.  I'm positive I didn't somehow mark it for formatting.  Besides, if it had somehow been formatted, it wouldn't show as "unallocated" would it?
actually, the partition would show up as unallocated if you had formatted it.
pablo is right. backup everything to an external hdd and reinstall everything.

---

