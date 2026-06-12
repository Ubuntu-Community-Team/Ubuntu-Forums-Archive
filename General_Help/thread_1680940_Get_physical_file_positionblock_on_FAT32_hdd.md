---
title: "Get physical file position/block on FAT32 hdd"
date: 2011-02-03
forum: General Help
---

### Post by 2Ub5N on 2011-02-03
Hi,
Im looking for solution how to find physical position/block of specified file on FAT32 partition. I have damaged hdd (I can mount partition and I see files) and im using gddrescue to make 1:1 copy, but i need only specified file. 
So I would like use gddrescue with -i pos switch, but I dont know how to get that position for specified file.
```

-i pos
--input-position=pos
Starting position in input file, in bytes. Defaults to 0. In fill mode it refers to the original input file
```
Thank you very much for any help.

---

### Post by psusi on 2011-02-03
If you only want the one file, then just mount the drive and copy that file off.

And this doesn't have anything to do with Assistive Technology and Accessibility.

---

### Post by s.fox on 2011-02-03
Thread moved to [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")

---

### Post by 2Ub5N on 2011-02-03
Sorry for wrong category, i hope someone help me to move it to right forum.

I cant copy it, because my hdd is damaged. Its a wedding move (~3Gb). gddrescue can copy that but its very slow. One day is 1Gb copy. I have 300Gb partition so this is too long for me. Im looking for solution how to get physical position of that file and start gddrescue with -i pos switch.

---

### Post by psusi on 2011-02-03
What *exactly* do you mean you can't copy it?  Can you mount it?  Can you find the file?  Does it just get an IO error when you try to copy that specific file?  If so, then ddrescue isn't going to be able to get it either, but you can try running it on that specific file rather than the raw disk.

---

