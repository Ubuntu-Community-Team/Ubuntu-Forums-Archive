---
title: "Recovering files on windows - Documents and Settings folder is a file"
date: 2011-07-25
forum: General Help
---

### Post by System Monitor on 2011-07-25
I am attempting to recover files from my hard drive because somehow my computer is unable to boot. I have tried everything, and I took it to the geek squad and they agreed with assumption that some critical file in windows must be corrupted preventing it from booting.


I have successfully booted up into the Ubuntu 11.04 Live CD. When I click on my hard drive under places in order to recover and copy the files to a thumb drive it opens up the root file system of windows (xp). Oddly, the should-be folder "Documents and Settings" is a file. I try clicking on it and it says that Ubuntu does not know which application to open it with. I tried cd-ing into it with the terminal using quotes and that didn't work either.

How can I access the files in the Documents and Settings folder? I need to be able to back them up.

Thanks.

---

### Post by Mark Phelps on 2011-07-25
Given all the problems, it really looks like your Windows filesystem got corrupted.  This could also be an early sign of hard drive failure.

And, the more you mess around with this in Ubuntu, the more likely you are to be unable to recovery anything.

You could try hooking your drive up to a Windows PC and run CHKDSK on it -- but be aware, that if there is substantial filesystem damage, that's likely to orphan the files.

You could also try hooking your drive up to a Windows PC, downloading and installing GetDataBack for NTFS from Runtime Software (on that PC), running that utility -- and seeing what it finds.  You would need to run it overnight most probably, to let it do a thorough search.  IF it finds the files you want, you will have to purchase it to do the actual file recovery.

---

### Post by alphaamanitin on 2011-07-25
My understanding is that if you are having input/output errors attempting to recover data from a drive can lead to even increased damaged.  If I were you I would read as much as I could then decide if I thought it safe to make a clone of the hard drive.  If I felt it was safe I would buy a drive of equal size to the original, I would clone my drive to it and work on that drive.  

Id

---

