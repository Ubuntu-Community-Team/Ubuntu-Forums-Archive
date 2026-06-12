---
title: "All cap file names being changed to all lower case"
date: 2005-03-03
forum: General Help
---

### Post by charlie763 on 2005-03-03
I use a Nikon 5200 camera as my SD card adapter. I checkout a CVS repository on to the card using the command line. When I take the SD card and read the repository on my windows computer at work the directories named "CVS" and the files "README, "TODO," and "DESIGN"  are in all caps as they should be. But when I mount the SD card back on my linux machine the files are shown as "cvs" and the files "readme," "todo," and "design" respectivly.

Also, when I do a "$ mkdir TEST" the file system shows the driectory as "test." This is causing me a problem because I need my files to keep their original name so I can use CVS with them. Please help. *tears*

---

### Post by alastair on 2005-03-04
The SD card is probably a FAT filesystem - probably mounted as type "vfat" in Linux.

man mount

Look at the section for "vfat" and :

shortname=[lower|win95|winnt|mixed]

---

