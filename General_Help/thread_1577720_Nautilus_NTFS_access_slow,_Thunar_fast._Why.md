---
title: "Nautilus NTFS access slow, Thunar fast. Why?"
date: 2010-09-19
forum: General Help
---

### Post by WittFan on 2010-09-19
I currently have a clean install of Lucid on relatively new hardware. When using Nautilus to access an NTFS partition, on either a local disk or a USB disk, it takes a long time (15-30 seconds?) to open each folder. However, once the folder is open copying files to and from that folder shows no delay. Strangely enough, there is no delay listing folder contents when opening NTFS folders using Thunar or listing a directory's contents from the command line.

Does anybody else have this problem? Any suggestions for troubleshooting it?

---

### Post by WittFan on 2010-09-23
FWIW, I tried running nautilus from a command prompt to see what kind of debugging output it gave. Unfortunately there was no output at all.:(

---

### Post by wilburg on 2010-10-22
Nautilus 2.32.0

Load times
10-30    seconds /usr/share            333 entries
46-500+              /usr/share/doc  1,582 
120-165              /usr/bin             1,762
38-32                  /usr/lib64          1,685

90-100% CPU 

computer i7-980, 12 gig ram, 10.10, 2.6.35-22

If anyone knows a fix for this please post it.

---

