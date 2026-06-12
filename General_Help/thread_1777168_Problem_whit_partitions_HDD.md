---
title: "Problem whit partitions HDD"
date: 2011-06-07
forum: General Help
---

### Post by mister_anderson on 2011-06-07
hi guys, sorry for my bad english and sorry if i write in the wrong forum direction :p


So, i have a problem , i want to install windows 7 and remove my ubuntu, but i cant preformat my hdd, I tryed to do that whit Gpart and some other programs but i can'n do nothing , my DHH have only 1 partiotion, which is used by OS
Now i need Windows 7 and i cant install it, because my HDD is not correct formated and i cant add new partions 
Any ideas how to make new partition , because whit Gpart i cant add new's, most of options are inactive.
Now i use ubuntu 10.10

Regards  !

---

### Post by iclestu on 2011-06-07
> **mister_anderson said:**
> hi guys, sorry for my bad english and sorry if i write in the wrong forum direction :p


So, i have a problem , i want to install windows 7 and remove my ubuntu, but i cant preformat my hdd, I tryed to do that whit Gpart and some other programs but i can'n do nothing , my DHH have only 1 partiotion, which is used by OS
Now i need Windows 7 and i cant install it, because my HDD is not correct formated and i cant add new partions 
Any ideas how to make new partition , because whit Gpart i cant add new's, most of options are inactive.
Now i use ubuntu 10.10

Regards  !

guessing most options in Gparted are greyed out because you are accessing it from your ubuntu system which is running on the partition you want to change.

Doesnt the windows 7 installation format your drive anyway if you just want to entirely replace ubuntu?

---

### Post by seawolf167 on 2011-06-07
You won't need to format any partitions before installing Windows. The Windows installer will take care of all that for you when you go through the step-by-step installation process. If you specify partitions manually in the Windows installer, simply delete the Ubuntu partitions so they show as unallocated space, then create your Windows NTFS partitions in the unallocated space.

---

### Post by mister_anderson on 2011-06-07
when i'm in windows installer , the buttons format and delete are inactiv, when i click NEW , the f*n installer says that the disk is not in NTFS format , and i can't go ahead :guitar:

---

### Post by seawolf167 on 2011-06-07
You'll have to delete the existing partitions first before you can continue - ensure that you enter the "Manually Partition the Disk" option (or similar wording), then when you left-click the existing partitions you will be able to remove/delete them after which they will become unallocated space. There might even be an erase/overwrite and use the entire disk option - you could simply choose that one as well. Its been a while since my last Windows install so I'm not 100% sure on that last option.

---

### Post by iclestu on 2011-06-07
> **mister_anderson said:**
> when i'm in windows installer , the buttons format and delete are inactiv, when i click NEW , the f*n installer says that the disk is not in NTFS format , and i can't go ahead :guitar:

hmmmm - surely windows installer can just format any drive (tho it woudl nuke the data)?? Im really surprised by this....

Suppose as a workaround you could boot with a live cd like [parted magic]("http://partedmagic.com/doku.php?id=downloads"), run Gparted, unmount your hdd and format it to NTFS  then reboot and run the win installation again???

EDIT: I should stop replying because I keep crossing posts with someone more knowledgable - listen to Seawolf167!!!!

---

### Post by seawolf167 on 2011-06-07
No worries iclestu, other options/opinions are always good!

If for some unknown reason the Windows installer can't delete the partitions (which I doubt would happen - Windows like to delete and reformat *everything* in NTFS :P), booting off a LiveCD and using GParted would be the next best thing. You wouldn't even have to format it in NTFS though, since the Windows installer would probably take over and reformat anyways, simply deleting the partition table should be enough.

---

