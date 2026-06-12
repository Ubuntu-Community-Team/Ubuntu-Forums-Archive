---
title: "Repair recovered image files."
date: 2010-09-21
forum: General Help
---

### Post by hariks0 on 2010-09-21
Hi all, I have a crashed NTFS HDD from which I had successfully recovered the all type of files but they are not readable. Even thumbnails are not viewable. I have tried almost all image viewers and graphics programs of gnome and kde. In windows, picasa displays 'Invalid file' while opening the images. Some junk text is there in documents, PDFs and spreadsheets.

Thanks in advance for any help. :(

---

### Post by termin on 2010-09-21
there are two things possible 
1. the hard drive you recovered the files from is corrupted
2. you didn't set up the correct file-system in the installation (not likely but possible)

---

### Post by Mark Phelps on 2010-09-21
What utility did you use to "recover" the files from the drive?  Linux testdisk/Photorec? Or an MS Windows utility?

Either way, it looks like the filesystem was generally corrupted from the crash.

From personal experience, I've found the MS Windows utilities do the best job of recovering files from FAT/FAT32/NTFS partitions and Linux utilities do the best job of recovering files from Ext2/3/4 partitions.

IF you used a Linux utility to recovery files from an NTFS partitition, and the drive is still usable, you might have better results using MS Windows utilities to do the same recovery.  You can download a free trial version of GetDataBack for NTFS from Runtime Software.  It won't actually recover anything, but it will tell you what it finds and what your chances of successful recovery will be.

---

### Post by hariks0 on 2010-09-21
The HDD is not physically damaged though the file system seems to be corrupted. the software used was [Recovermyfiles]("http://recovermyfiles.com") and the files [.jpg, .xls etc] were previewed perfectly in the interface of that application.:(

---

### Post by hariks0 on 2010-09-22
:D It is solved. The actual problem was that the HDD went sleeping after a while by which time the program fetched the file list/details/preview. When I actually recover the files, the HDD is not accessible and the program recovers the files which contained only zeroes despite the file format. I changed the power option of Windows and tried again. Now the files are recovered without any problem.

Thanks for the replies and assistance. 

By the way, let me gratefully mention that the vendor of the above mentioned software provided online assistance via chat and I should be really thankful to them.

---

