---
title: "corrupt master file table"
date: 2011-07-22
forum: General Help
---

### Post by staylate on 2011-07-22
On my backup drive I can no longer see any files. According to Testdisk program the master file table (MFT) is bad. How do I restore or rebuild the MFT?
Thanks.

---

### Post by staylate on 2011-07-22
I forgot to add that Testdisk says that both the MFT and the backup MFT are bad. 

I ran the Easy Recovery Pro program, and all of my files are still there. If I can just rebuild or recover the MFT, I hope that my backup drive will be restored as it was.

Does anyone have any ideas, how to build or recover the MFT?

---

### Post by Mark Phelps on 2011-07-23
Some folks have used ntfsfix to repair NTFS problems -- but in my experience, the single BEST way to repair NTFS problems is to connect the drive to a Window PC and run CHKDSK.

---

### Post by staylate on 2011-07-23
Thanks for the suggestions. However, I have run ntfsfix from Ubuntu, and chkdsk /f /r from Windows XP, and still Testdisk says that both the MFT and the mirror MFT are bad.

I  know that my files are still on the drive that I am trying to recover, because I can recover most of the files with Easy Recovery Pro, or GetDataBack. The problem with this type of recovery is that the files are not organized in the folders in which the files were originally stored. I can recover about 4000 files, but they are not organized in a usable way. Anyway, I don't remember exactly where each one of the files belongs. Doing a recovery without the folders is a big, unorganized, mess.

I am hoping to find a program that will repair or rebuild the MFT, by using the existing file data.. Ntfsfix and chkdsk won't do that.

staylate

---

