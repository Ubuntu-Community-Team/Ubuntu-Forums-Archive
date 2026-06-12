---
title: "Data recovery for NTFS"
date: 2010-10-24
forum: General Help
---

### Post by diablo75 on 2010-10-24
I don't want to go into too much boring detail about what happened, but here's the short story:

I have an NTFS partition on my computer that dual-boots with Ubuntu.  The NTFS housed Windows XP, until yesterday when the stability of the NTFS file system was tested with the creation and deletion of millions of temporary files during a data recovery from someone elses hard drive.  I was using Runtime's Get Data Back for Windows (for NTFS) and its scan results on their hard drive returned dozens and dozens of duplicate entries for the same files, probably because when a hard drive is defragmented, files get shuffled around so it was actually detecting the real files, and seemingly endless number of duplicates.

So I don't really know exactly what happened but when I rebooted the computer after letting it do this for 2 days strait before I said, "This shouldn't be taking so long to finish..."

One particular thing that was weird (while I still had the OS running) was that if I looked at the properties of a folder created by GDB after copying files from the failed drive, it would tell me that a seemingly endless number of files were inside the folder (it'd never stop counting), when it actuality only contained a small number.

I did a chkdsk on the hard drive using a BartPE boot CD and that repaired a few errors but then the file system appeared to contain nothing at all.  I'm sure the data is there, but that the file index/table (whatever it's called) is corrupt.

I've got Ubuntu running along side this partition and was hoping to find a Linux based data recovery program that might be able to find these missing files back, saving me the trouble of taking the drive out of the machine and hooking it up to another Windows computer; GDB doesn't work in WINE (although I bet with the right tweaks it could; it just doesn't see the partition/drive).

---

### Post by aysiu on 2010-10-24
Install the *testdisk* package and then run ```
sudo photorec
``` You'll need an external hard drive to back up the recovered files to.

---

### Post by diablo75 on 2010-10-24
I seem to be having some trouble with photorec.  I get to the point where I can see all the partitions on my hard drive, including the NTFS partition, but when I select it by pressing Enter, it seems to show me contents of the files that are actually in my home partition for Linux.  Am I doing something wrong?

---

### Post by MarkAlter on 2010-10-28
Hello Diablo75,

Some times on fragmentation some of the files are missed then you face the situation that you could not access some programs and they give some errors. Now you have to use a efficient data recovery software for the purpose of recovering those missed files and for the same you need a good data recovery software. You should try Kernel for FAT and NTFS data recovery software for the recovery of those important files. If will run in Windows mode and in the demo version of the software you can preview the lost files which are required for those applications.

Thanks

---

