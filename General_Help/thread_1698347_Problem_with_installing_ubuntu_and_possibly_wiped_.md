---
title: "Problem with installing ubuntu and possibly wiped hdd?"
date: 2011-03-02
forum: General Help
---

### Post by Gizmou on 2011-03-02
Hello there,
 
Yesterday was the day I decided to step unto ubuntu path and dual boot it with xp on my hp mini 311. After trying to boot it 10.10 using UNetbootin(from HDD) and not making any backup(I know I know,stupid mistake) the installation process didn't find my hdd.
 
Several google searches revealed trying su sudo , fdisk - l and drmraid -E -R /dev/sda in terminal. As a complete noob in linux I wen't with the flow,not knowing what these cmds do. Terminal responded with error that it could not find my /dev/sda hdd(even though the f-dsik -l command clearly showed my hdd was a). 
 
Further seaches revelead I should try switching my hdd from nfts or ahci to other formats for the time of installation. Unfortunately, after not considering once more what it could do to my hdd and not finding this option in bios I switched my hdd from nfts to journal mode in the disk managment application in ubuntu,which resulted in some kind of error.
 
Next,I wen't into the installation process once more and of course ubuntu recognized my hdd for this time but showed the options to use the whole hdd or partion it i.e. showing that it's completaly clean and without any sign of my windows xp.
 
I panicked and restarted my pc to find the message - no operating system installed.
 
So basically my question is - is it possible to recover my probably wiped documents,downloads and anything I had on my xp,or is it a start from scratch now?
 
What should I do if I encounter the problem once more of ubuntu not finding my hdd,or possibly it will find it now as nothing is installed on it?
 
It seems that now I have no choice but to completaly switch to ubuntu as I can't install xp from usb,if everything has been wiped,so maybe there's a good side to this too?
 
Thank you for reading this ridicilously long post to end and I hope you can provide me with answers to my questions.
 
Thanks,Gizmou

---

### Post by mikewhatever on 2011-03-02
> I switched my hdd from nfts to journal mode in the actual ubuntu installation

Not quite sure what that means, looks like you've formatted the Windows partitions. Can you post the output of 'sudo fdisk -l' to verify the partition layout.

---

### Post by Gizmou on 2011-03-02
Sorry,I meant - the disk managment option in the ubuntu applications,not actual installation process if that helps.Unfortunately,can't post sudo fdisk -l option as I am not home atm.Also can't access ubuntu now,as I booted it from hdd that time and now it just shows -no operating system,though I will load through usb later today.
 
But as I mentioned,after getting the error the installation app(the one icon you see when you boot ubuntu through live cd -hdd in this case) showed the options of using the whole hdd to install ubuntu or make partition and when I selected to make partitions(as I though xp is still there) the whole hdd appeared without any and completaly clean.Hope that helps,to establish if I can get any files back or have I completaly wiped xp out?

---

### Post by mikewhatever on 2011-03-02
Hopefully, the output will show what partitions are on the hdd, as the Ubuntu installer sometimes fails to see the existing partitions. If you really formatted everything, tesdisk could probably recover the files. The problem with testdisk is, it doesn't recover file names.

---

