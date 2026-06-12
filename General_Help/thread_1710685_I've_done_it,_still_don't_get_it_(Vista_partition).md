---
title: "I've done it, still don't get it (Vista partition)"
date: 2011-03-20
forum: General Help
---

### Post by egkeat on 2011-03-20
After leaving Ubuntu over frustrations with my Wubi install, I have returned, doing a Vista partition and installing Ubuntu 10.04. I'm looking at the Vista disk management now and have four sections...
426 ntfs, 28gb primary, 1.28 primary, and factory image 9.43. When installing Ubuntu, I selected installing into largest free space. Now the 28gb and 1.28 show 100% free space. Where's Ubuntu? I really don't get this partitioning thing at all.:confused:

---

### Post by mr.farenheit on 2011-03-20
i don't know if it would work, but you could try moving the vista partition in live mode then move all the unallocated and unused space in one spot then try reformatting it for linux.

---

### Post by Script Warlock on 2011-03-20
you cant view ubuntu partition using windows vista..

---

### Post by cptrohn on 2011-03-20
Windows partitioning tools won't see ext4.....  I would download Gparted live (it runs as a live CD) and run that and it will show you your partition tables better.

---

### Post by Mark Phelps on 2011-03-20
If you still want to use Vista, do NOT, repeat NOT, move it around using any Linux utilities. Doing so will likely corrupt the filesystem, rendering it unbootable.

Also, it looks like you may have reformatted your Vista partition(s) as a byproduct of installing Ubuntu. To see if this is what happened, try rebooting into Vista and confirming it will run.

---

### Post by jerome1232 on 2011-03-20
> **cptrohn said:**
> Windows partitioning tools won't see ext4.....  I would download Gparted live (it runs as a live CD) and run that and it will show you your partition tables better.

Windows will still see the partitions though. Give us a screenshot of gparted or the output of fdisk from a live cd so we can better direct you on idea's for a partition layout that would work for you.

I included some screenshots of my setup, as seen from Windows 7. The two primary partitions at the end are my /boot and / partitions for Ubuntu. Gparted has a much nicer easier to understand output though.

If you want to give us the output of fdisk in addition to gparted you can. :)

from a live cd
```
sudo fdisk -l
```

---

### Post by egkeat on 2011-03-20
Okay, thanks all for your help. I kinda figured I couldn't move things around anyhow--especially since I don't have much knowledge of this would screw things up more than likely. 

I'd tried several times in the past to do a gparted installation and it just messed things up, so after looking around, I discovered that Vista doesn't like any other partition managers very much so I used its service and worked well enough.

I didn't realize the Ubuntu partition wouldn't show up in Vista...but now that makes sense....:)

---

### Post by egkeat on 2011-03-20
Thanks for the screenshot. Looks about like mine....not feeling so confused now.

---

