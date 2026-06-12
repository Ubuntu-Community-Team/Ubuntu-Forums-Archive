---
title: "Formatting help"
date: 2009-08-01
forum: General Help
---

### Post by kajankow on 2009-08-01
Hey guys.

I have a PC that had window vista on it. i was playing around and i decided i enjoyed ubuntu alot so i wanted to partition my internal hard drive so i can switch back and forth between the two operating systems. (vista and ubuntu) i accidentily left no room for windows and erased windows completely. 

i now have my vista cd and tried to do a clean install to my computer. well when i get to a part i need to pick where i need to install windows. windows can only be installed if the hard drive is in NTFS format. i have gparted with ntfsprogs installed. can someone tell me what to do next so i can get windows back on my computer. i dont have any important data or anything on my internal hard drive now so a complete erase will be fine (if that is my next step)

---

### Post by merlinus on 2009-08-01
Run gparted, look for the first primary partition (or it may now be unallocated space at or near the front of your hdd), and format it as ntfs.

If you need more, post a screenshot of gparted.

---

### Post by kajankow on 2009-08-01
ok here is what i have. i know u have to unmount it i believe but it wont because of the / or something like that. it says i can make a new table under the device option. is that what im shooting for?

---

### Post by shp on 2009-08-01
Looks like you didn't leave any space for windows.
You'll have to resize your linux partition using the live cd or reinstall it with a smaller partition.

---

### Post by kajankow on 2009-08-01
which live cd? the gparted cd or my ubuntu live cd?

---

### Post by shp on 2009-08-01
oh gparted although either would work.

just resize it to leave empty space. dont bother formatting it as ntfs as its better to let the vista install do that.

---

### Post by kajankow on 2009-08-01
ok so if i put in my ubuntu live cd i can repartition my hard drive? would i just redo an install  and do a manual partition? 50% 50% 

if that works can i completely get rid of ubuntu later and get the space back for windows?

---

### Post by merlinus on 2009-08-02
You can use gparted from the ubuntu live cd or its own live cd to shrink sda1 and make room for vista.  Then you can install vista into the unallocated space.

There is no need to reinstall ubuntu.

---

### Post by kajankow on 2009-08-02
ok i will try that in the morning. Thanks again for all the help.

---

### Post by kajankow on 2009-08-04
Thank you guys so much. it all came together and now i have my old computer back. it is actually faster than before. thanks again, you guys are awesome.

---

### Post by merlinus on 2009-08-04
Excellent news!  Have fun...

---

