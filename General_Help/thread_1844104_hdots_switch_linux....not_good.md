---
title: "hdots switch linux....not good"
date: 2011-09-14
forum: General Help
---

### Post by Levitys on 2011-09-14
ok guys i have run into another problem...

i added 2 new hdd to the mix so now i have 4.
1 seagate (os)
2 hitachi 
3 wd20
4 wd10

now they are in that order in bios and motherboard but when i boot into linux the wd20 is in the second slot.
The problem being my xbmc has the hitachi at sdb1 and now thats where the wd20 is.
so i guess my questions are.....
why did this happen and how do i fix it?

any help would be appreciated

thanks
levitys

---

### Post by kimda on 2011-09-14
Can you tell in xbmc the new location of your harddrive which was first on /dev/sdb1? You can go into ubuntu and find out its new location or perhaps you can do this directly in xbmc. 

Or you could try switching the sata cables with the harddrive which is now discovered as /dev/sdb to get the drive back at /dev/sdb.

---

