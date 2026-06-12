---
title: "Renaming Files Irritant"
date: 2009-10-06
forum: General Help
---

### Post by joeyknuccione on 2009-10-06
A minor irritant, but...

Say I have a file named:

this name.mp3 <little letters

And I want to change it to:

This Name.mp3 <capital letters

I get "this file already exists" error.

So, I have to do:

ThisName.mp3 <no space or some such

Save it, then change it again to:

This Name.mp3 <capitals corrected

Question:
Is there a way to force Ubuntu to differentiate between capital letters in this regard?

---

### Post by Onesimus on 2009-10-06
I am using Ubuntu 8.10, and it works just as you would like it to work.  What version of the OS are you using ?

---

### Post by Onesimus on 2009-10-06
Also what are you using to rename the files ?  Is it Nautilus, the command line, some other file manager ?

A few more details about the nature of your problem would be really helpful, if you would like your problem solved.

---

### Post by Giblet5 on 2009-10-06
You will only get this error if you are attempting that command on an NTFS or FAT filesystem where case-sensitivity is not really supported.

That's a shortcoming of NTFS and FAT filesystems.

Solution: Perform that command on an EXTn filesystem, or perform multiple steps for each file on NTFS or FAT.


Add iso9660 filesystems (commonly used on CD and DVD) to the "That won't work" category.

---

### Post by KeyserSoze93 on 2009-10-06
Linux shouldn't have an issue about the case in filenames; "this file" and "tHIS FiLE" are always different files.

Are you renaming files in the terminal, or using a file browser, because some applications might kick up rough (though I'd be surprised if nautilus does, since it is a Linux app from the ground up)

Mind you, if you aren't using a POSIX filesystem (i.e. if the file is on a Windows NTFS drive or an MP3 player - which usually uses FAT32), then there could be an issue.

I recently had a problem where I had two files on an (ext3) samba share called TV_Sorted and TV_sorted.

Ubuntu knew they were different, but the Windows client I was using saw both files, but only opened one (when either was selected, i.e. it treated them like two aliases for the same file.)

---

### Post by joeyknuccione on 2009-10-06
I 'preciate the many and fast responses.

My problem is on a FAT32 file system I use for compatibility with the OS that shall not be named (work comp), so I'll deal with it. I'll mark it solved.

Many thanks!

UBUNTU ROCKS!!!!!!!!!!!

---

### Post by Giblet5 on 2009-10-06
> **KeyserSoze93 said:**
> Mind you, if you aren't using a POSIX filesystem (i.e. if the file is on a Windows NTFS drive or an MP3 player - which usually uses FAT32), then there could be an issue.

NTFS is POSIX-compliance-capable. Just ask Microsoft.

In fact, Microsoft will tell you how they invented the POSIX standard and that you owe them money for discussing it.

---

