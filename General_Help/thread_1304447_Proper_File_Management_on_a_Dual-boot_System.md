---
title: "Proper File Management on a Dual-boot System"
date: 2009-10-29
forum: General Help
---

### Post by steve8091 on 2009-10-29
I've done a bit of searching, but haven't come up with much discussion on the subject. I'm a Linux noob, but I've been around computers for quite a few years, beginning with DOS back in the old days, so I've got some small (though likely outdated) idea of what I'm doing.
 
I just created my first dual-boot system using Ubuntu 9.04 and Windows 7. What I'm looking for are suggestions on how to best manage files on a dual boot system. I'd like to be able to view and edit my documents (music, movies, photos, docs, spreadsheets, etc) from either OS. I plan to use many of the same programs (Inkscape, OpenOffice, etc) on both OS's, as I've been using most of those in Windows already.
 
Will locating all of "my documents" for both OS's on a single hard drive or partition create issues for me? Is there any value in locating these documents on a separate hard drive versus a separate partition? Are there particular file types that are prone to issues?
 
Thanks in advance.

---

### Post by DoctorMO on 2009-10-29
I don't know how flexible windows 7 is when it comes to where it places it's documents. Your only concern will be how effectively the home directory mount conflicts with the my documents location.

Firstly, because windows 7 doesn't support ext file systems, you'll have to make a FAT32 or NTFS disk partiton and you'll need to make sure ubuntu munts the partition in the same place on boot, then create a symbolic link from your Documents directory in ubuntu, to your documents directory on the FAT or NTFS partition.

This should have the desired effect, while not mixing the configs of each system. Good luck, it's hard to reconcile these two different platforms, mostly because windows doesn't ever want to share.

---

