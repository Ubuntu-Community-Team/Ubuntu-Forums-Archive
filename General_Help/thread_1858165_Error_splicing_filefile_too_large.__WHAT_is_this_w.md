---
title: "Error splicing file:file too large.  WHAT is this weird error?"
date: 2011-10-11
forum: General Help
---

### Post by pretty_whistle on 2011-10-11
I have a portable drive where I save disk images.  I successfully copied two Ubuntu disk images to this drive but get this error when trying to copy the Windows disk image folder:

[IMG]http://i53.tinypic.com/2ewir6s.png[/IMG]

Why is it talking about splicing it when I'm not trying to splice anything.  I am trying to copy the folder from the desktop to this drive.

It's also not too big.  The drive has 250GB of space and the folder is only 20GB.

Also note:  I did not get this before when the portable drive was NTFS.  But then I formatted it to FAT32 and get this same error on the same folder every time.

What's going on??

---

### Post by pretty_whistle on 2011-10-11
I doubt formatting the drive to another file system caused it directly.  It's probably the .adi file not liking it when I copied it from the drive to the desktop for safekeeping while I formatted the drive.  It probably broke it or something so now it can't copy back to the drive.

Am I right?  It has to be since everything else I copy to the drive is fine.

---

### Post by oldos2er on 2011-10-11
I think FAT32's file size limit is 2 GB.

---

### Post by pretty_whistle on 2011-10-11
> **oldos2er said:**
> I think FAT32's file size limit is 2 GB.

I've heard that someplace.  I thought it was a joke.

How can they sell flash drives that are 64GB if it's really only a 2GB?

---

### Post by Doug S on 2011-10-11
How big is the file? FAT32 has a per file size limit of 2**32-1 or 4,294,967,295 bytes.

---

### Post by pretty_whistle on 2011-10-11
> **Doug S said:**
> How big is the file? FAT32 has a per file size limit of 2**32-1 or 4,294,967,295 bytes.
It's 20.2GB.

---

### Post by cryptotheslow on 2011-10-11
The flash drive is 64GB. When it is formated as FAT32 you can still store 64GB of stuff on the drive - just no individual file can be larger than 4GB.

Unless you can bring your image file down under 4GB then you will have to use a different format on the drive. MS released an "exFAT" format for WinXP that is FAT based but allows larger filesizes. I've not seen a Linux flavour of that format - but then I can honestly say I've never really bothered looking! :D I vaguely remember there is some read support for exFAT with Linux but no write support as yet.

---

### Post by pretty_whistle on 2011-10-11
FAT32 file size limit?  I presume FAT is not much different....??

---

### Post by Doug S on 2011-10-11
You can have several files and fill up the flash drive

---

### Post by pretty_whistle on 2011-10-11
It's beginning to sound like I should've left it as NTFS..... and I should format it back.......

---

### Post by pretty_whistle on 2011-10-11
> **cryptotheslow said:**
> The flash drive is 64GB. When it is formated as FAT32 you can still store 64GB of stuff on the drive - just no individual file can be larger than 4GB.

Unless you can bring your image file down under 4GB then you will have to use a different format on the drive. MS released an "exFAT" format for WinXP that is FAT based but allows larger filesizes. I've not seen a Linux flavour of that format - but then I can honestly say I've never really bothered looking! :D I vaguely remember there is some read support for exFAT with Linux but no write support as yet.

Oh.  Well then NTFS here I come!

---

### Post by cryptotheslow on 2011-10-11
Probably going to be the only sane way forward depending on your use case. Only scenario I can think of where it may not be would be if you are simply using the USB drive to transfer the files to another PC, in which case you could get away with slicing the files up into <4GB chunks and reassembling them on the destination machine. Even then it's less hassle just to use NTFS.

Why did you choose to reformat from NTFS to FAT32 in the first place?

---

### Post by pretty_whistle on 2011-10-11
> **cryptotheslow said:**
> Probably going to be the only sane way forward depending on your use case. Only scenario I can think of where it may not be would be if you are simply using the USB drive to transfer the files to another PC, in which case you could get away with slicing the files up into <4GB chunks and reassembling them on the destination machine. Even then it's less hassle just to use NTFS.

Why did you choose to reformat from NTFS to FAT32 in the first place?

I thought that not all systems would detect a removable drive if it were NTFS so I changed it over.

---

### Post by pretty_whistle on 2011-10-11
Update:

Formatting the drive as NTFS has solved the issue.  Everyone was correct when you said the FAT32 was causing it because my file was too large.

---

