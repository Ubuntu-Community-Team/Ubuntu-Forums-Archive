---
title: "Any Benefit to Wiping Hard Drive?"
date: 2010-09-17
forum: General Help
---

### Post by cottfcfan on 2010-09-17
Because I install/uninstall a fair few operating systems, I occasionally run Kill Disk off Hirens Boot CD to clean my drive.
Being a 500GB Drive this takes about 12 hours.
Is there any benefit to doing this? ie. drive longevity, speed, etc
or am I wasting my time?

---

### Post by endotherm on 2010-09-17
> **cottfcfan said:**
> Because I install/uninstall a fair few operating systems, I occasionally run Kill Disk off Hirens Boot CD to clean my drive.
Being a 500GB Drive this takes about 12 hours.
Is there any benefit to doing this? ie. drive longevity, speed, etc
or am I wasting my time?
unless you are worried about sensitive data that you have previously deleted but not overwritten, then it probably isn't an issue. in fact an intense long running operation like a cryptographic wipe will put additional wear and tear on the unit, decreasing the liftspan (albeit not noticably) so I would just do a format and be done with it.

---

### Post by Simian Man on 2010-09-17
Why *would* there be any benefit?

---

### Post by srs5694 on 2010-09-17
I can think of two possible benefits, beyond the security issue that endotherm mentions:


[list]
[*]If you *don't* blank the disk and then lose data (trashed partition table, accidentally deleted files, etc.), recovery tools like TestDisk and PhotoRec might get confused by old data from before the latest repartitioning operation, thus making it harder to recover data or making it likely that old unwanted files will be recovered along with new files.
[*]Some types of whole-disk imaging utilities, such as dd, will back up everything, including blank sectors. When compression is applied, if those "blank" sectors contain old data, they won't compress as well as they would if they really were blank (containing "0" values), thus increasing the size of your compressed backup image.
[/list]


If you're using the disk for test installations, as it sounds like you are, then I doubt if either of these advantages is a significant one, so I wouldn't bother blaking the disk, given the time investment and, as endotherm says, the extra wear and tear on the disk that blanking it causes.

---

### Post by cottfcfan on 2010-09-17
Thanx for your quick responses.
Think i'll just reformat in future.

---

### Post by dcstar on 2010-09-18
> **cottfcfan said:**
> Thanx for your quick responses.
Think i'll just reformat in future.

That might upset those people who wear metal film on their heads so the CIA/MI5/aliens etc can't read their brainwaves - they ALWAYS wipe their hard drives (apparently they sleep better afterwards......)     :roll:

---

