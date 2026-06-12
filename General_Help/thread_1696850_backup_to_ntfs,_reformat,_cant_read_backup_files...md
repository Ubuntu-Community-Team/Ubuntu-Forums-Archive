---
title: "backup to ntfs, reformat, cant read backup files..."
date: 2011-02-28
forum: General Help
---

### Post by thewooleymammoth on 2011-02-28
I screwed up things to the point where it was easier to reinstall ubuntu than to try and fix it. I opened the tar file with archiver to make sure it worked. it did.

I backed up all of my stuff in a tar.gz file and placed it in my windows hard drive (dual boot), I also made a folder in the c:/ drive. Then i reinstalled ubuntu.

After the reinstall, i went to pull the info back off the other drive and archiver gave me an error when trying to open it. I cant remember exactly what it said sorry. Tried with archiver and Xarchiver. No luck

Rebooted into windows and tried to open the file with winrar and got an error, so i tried to open the folder and it said it was unavailable. Then the files were gone. ?????????

Tried to boot into linux too see if the files were still there in ubuntu and they were gone....

It's not ultra important to get those files back but it would be much more convenient. Any ideas on what happened/ways to fix it?

---

### Post by thewooleymammoth on 2011-02-28
thought of a potential factor?

My old home directory was encrypted with lvm and this one is not?

---

### Post by tristone on 2011-02-28
This sounds very much like corrupted fs entries. The write feature for NTFS module is often marked as "experimental" in linux. How about running disk scan and repair tool in windows? It may give you back your file or it may clean it up as garbage.

If the files are really important then it will be best to take a complete dump of that partition as soon as possible.

---

### Post by thewooleymammoth on 2011-02-28
eh, over it. My brother turned on the computer and let it boot into windows and it did do a ntfs integrity check. I cant seem to find any way to find that the files even existed. The tar.gz file was like 12 gigs and the drive claims to have that space back. I think they were lost to a point to where it would be to inconvenient to try and recover. What i really wanted out of there was system tweaks and fixes. Oh well i've recreated most of them already. It only took a few files.

Thanks for the reply! I'll make sure to watch out for that in the future.

---

