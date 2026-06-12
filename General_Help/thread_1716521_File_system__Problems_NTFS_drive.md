---
title: "File system  Problems NTFS drive"
date: 2011-03-28
forum: General Help
---

### Post by dwlamb on 2011-03-28
A drive on my Linux machine is NTFS as the file system.  There's a file corruption issue of some kind for copying files from the drive to another or another PC result in I/O errors.

Overall, I work with 2 systems, one Windoze, the other Linux.  I'm about to switch the roles of the 2 machines.  The one with the corrupted ntfs partition is about to become my Windows machine and the Windows machine is going to become Linux.

Since I will be installing Windows on the machine with the problematic ntfs partition, I'm figuring at some point, Windoze chdsk will kick in and fix the drive.  (Windows will be installed to another drive that is perfect right now.)

Is this a correct assumption?  Or, do I do everything I possibly can to fix the corrupt partition prior to the new Windows install?  If this is true, what are my options for fixing corrupted files under Ubuntu?

Research I've done hasn't yielded much in results and a definitive answer for fixing corrupt files in Linux.

---

### Post by coffeecat on 2011-03-28
Basically, if you have a corrupted NTFS filesystem you need chkdsk to repair it. There is no Linux tool that can replace chkdsk. From man ntfsfix:

>  ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.
I don't know about Windows automatically chkdsk-ing the partition once it's installed. You might want to run chkdsk from the repair console of a Windows install disc or hook the drive up to a Windows system in order to run chkdsk first.

---

