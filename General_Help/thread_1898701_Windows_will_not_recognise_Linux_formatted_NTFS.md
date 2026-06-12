---
title: "Windows will not recognise Linux formatted NTFS"
date: 2011-12-21
forum: General Help
---

### Post by RefinersFire on 2011-12-21
I formatted an EXT2 partition to NTFS using Ubuntu 11.04 and my Windows 7 install (I need to use Windows sometimes) will not recognise it. What am I missing? Could it be that the partition is on a Linux HDD and Windows 7 is on another HDD? The partition is bigger than the Windows HDD.

---

### Post by crazy bird on 2011-12-22
Windows was and still is not able to read/write Linux formatted drives. You need a tool for Windows to be able to read/write Linux formatted drives: [http://www.google.nl/search?q=ext2+reader+windows&hl=nl&source=hp&gbv=2&gs_sm=e&gs_upl=1047l8984l0l10187l20l17l1l1l1l0l312l2544l0.8.5.1l14l0&oq=ext2+reader&aq=1&aqi=g1&aql=]("http://www.google.nl/search?q=ext2+reader+windows&hl=nl&source=hp&gbv=2&gs_sm=e&gs_upl=1047l8984l0l10187l20l17l1l1l1l0l312l2544l0.8.5.1l14l0&oq=ext2+reader&aq=1&aqi=g1&aql").
 
You can find a solution here.
 
 
And why formatting to ext2?? That's an old standard. Better is to use EXT3 or EXT4.

---

### Post by mastablasta on 2011-12-22
he formated an old ext2 into NTFS. windows should be able to read NTFS, right?
 
i have no idea what went wrong, however since you just formated it you could do a quick format again using windows disk manager. after that it should be read.
 
another option is that windows simply didn't mount it or that windows can't read the parittion table on that disk (can't find where the partition starts). this can be solved using partition doctor or similar tools.

---

### Post by mcduck on 2011-12-22
> **RefinersFire said:**
> I formatted an EXT2 partition to NTFS using Ubuntu 11.04 and my Windows 7 install (I need to use Windows sometimes) will not recognise it. What am I missing? Could it be that the partition is on a Linux HDD and Windows 7 is on another HDD? The partition is bigger than the Windows HDD.

Does the Disk Management in Windows recognize that partition and display the correct file system for it? Could it be that it's actually working, and you just need to assign a drive letter to the partition...

---

### Post by Mark Phelps on 2011-12-22
While Windows SHOULD be able to read an NTFS format drive, when formatted from Linux, the Windows installers generally work best when you allow THEM to format the partitions.

I found this to be the case years ago with Vista, and it continues to be the case with Win7.

---

