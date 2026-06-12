---
title: "Access Windows files from Ubuntu on parallel OS configuration"
date: 2012-02-12
forum: General Help
---

### Post by nick roto on 2012-02-12
I have a RAID 1 system for my Win7. On the same computer I have a third  disc, not part of the Raid, on which I have installed Ubuntu 11.10. I  choose which OS to boot into at startup. From Ubuntu I can see the Raid  discs and access folders and open files (not the other way around, from  Win to Ubuntu).
At one point I cut and pasted some files from my Ubuntu file store into a  folder on my Win system - I couldn't see them when I returned to  Windows but unfortunately I can't see them from Ubuntu either any more.  Maybe I need to transfer files via memory key in future but in the  meantime I have lost some files. Can anyone tell me where they might be  or whether they are recoverable?

[I don't know whether the RAID configuration is the significant factor here, after all I only copied the files to one of the Raid pair and I'm not sure how it liked that. No faults reported back on Win though.]

---

### Post by btindie on 2012-02-12
Use [this]("https://help.ubuntu.com/community/Installation/SoftwareRAID") link as a starting point, it's likely that you're using FakeRAID.

---

### Post by nick roto on 2012-02-12
Thanks Btindie, but I'd rather not make any changes to the Raid system from Ubuntu.
Essentially I have two distinct systems that happen to share the same hardware, apart from their HDDs, and I want to keep them separate except for copying the occasional file. I hadn't expected Ubuntu to be able to understand my Windows file system but since it did I thought that would be a quick way of transferring files from Ubuntu to Windows; it's not something I need to do a lot. My only problem is to find the files that have fallen into a dark place, if possible.

---

### Post by btindie on 2012-02-12
OK, so the RAID appears to work fine? Your RAID disk shows up under Ubuntu..

It may have been a permissions problem but it's hard to say. If the files are not where they were originally then they may be gone. Until you know something like this works you're best to copy instead of move which is the equivalent to copy + delete orig.

I would imagine that your windows partition is NTFS, this does work r+w using the ntfs-3g file system but it may take some configuration for user permissions. You'd be better of with creating a small FAT32 partition under windows and use that for transferring files between the two OS's as that way you don't get any permission issues.

You could try first by copying over some test files. Do this from the terminal and you'll see any error messages if there's a problem. As an example:
```
cp -v ~/Documents/test.pdf /media/WIN7/Documents/USERNAME/
sync
ls -l /media/WIN7/Documents/USERNAME/*.pdf
```
to check that it worked from the Ubuntu side. Then boot into windows and see if the file is there and accessible.

---

### Post by nick roto on 2012-02-12
Thanks, I may try your suggestion (FAT32 partition). For now I'll probably use a memory stick as I don't think I'll be copying too many files.
It looks like I'll have to recreate the lost files though. Never mind, it's a shame but not a disaster, only an hour or so's work.

---

