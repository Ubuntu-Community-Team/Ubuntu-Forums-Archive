---
title: "No editing options available in gParted"
date: 2009-11-09
forum: General Help
---

### Post by OldGrantonian on 2009-11-09
I have dual-boot Vista and Ubuntu karmic. I want to reduce my Vista partition in order to increase my Ubuntu partition.

I unmount the Vista partitions and launch gParted. 

If I select a Vista partition to reduce, there are no editing options available. Only "Delete" is available.

Should I be doing this from a live CD?

---

### Post by Mark Phelps on 2009-11-09
If you have a Vista DVD handy and don't mind rebooting again and again to repair the Vista OS, then you can try the shrinking with GParted.  

But if you don't have such a DVD, You would do better using the Vista built-in Disk Management utility. That way, you won't have to worry about ending up with a corrupted Vista OS partition that then, will not boot anymore.

---

### Post by Aearenda on 2009-11-09
I suspect you need to install 'ntfsprogs' to enable NTFS partition editing in gparted.

---

### Post by jbrown96 on 2009-11-09
I would strongly recommend using Vista's disk management utility. If you really want to use gparted, then Aearenda's suggestion is probably right.

---

### Post by The Funkbomb on 2009-11-09
Do it from the Live CD.  You really can't mess with partitions when you're working from the same drive.

---

### Post by wojox on 2009-11-09
And make sure you Defragment Vista twice before you start shrinking. And yes you need to boot a live cd to shrink it.

---

