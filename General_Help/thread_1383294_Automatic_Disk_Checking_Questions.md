---
title: "Automatic Disk Checking Questions"
date: 2010-01-17
forum: General Help
---

### Post by eyeJ on 2010-01-17
I had bad experience with disk checking in windows. Boot checker just moved all more and more of my files to a hidden folder without me knowing. I lost a lot of photos due to this. Afterwards when I checked that folder I found that most of the files were intact and I was able to open them without a problem. How dumb is that a program moves files without your permition to do so :shock:
So I'm wondering what happens with files on Ubuntu if they get corrupted or are suspected as corrupted?
And how can I know if the automatic checking procedure that runs when booting found any corrupted files, bad sectors etc... ?

Thanks :)

---

### Post by fancypiper on 2010-01-17
Look in the lost+found folder for the partition.

[Linux Filesystem Hierarchy - lost+found]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")

---

### Post by jocko on 2010-01-17
> **eyeJ said:**
> I had bad experience with disk checking in windows. Boot checker just moved all more and more of my files to a hidden folder without me knowing. I lost a lot of photos due to this. Afterwards when I checked that folder I found that most of the files were intact and I was able to open them without a problem. How dumb is that a program moves files without your permition to do so :shock:
So I'm wondering what happens with files on Ubuntu if they get corrupted or are suspected as corrupted?
And how can I know if the automatic checking procedure that runs when booting found any corrupted files, bad sectors etc... ?

Thanks :)
I'm pretty sure that will happen even in linux filesystems (every partition have a "lost+found" folder, where such files will be placed).

One reason for this is that it's not always possible to know in which folder the original files were before they were lost. The physical filesystem is not as simple as a hierarchical tree of files and folders. One small part of the file system (file allocation table/master file table) contains information on file names and physical location of the data in each file, folder names and which file belongs in which folder, while the rest of the file system just contain the actual data.
So a file's imaginary location in the file system tree can be lost even if the file name and physical data is intact. The scanner would just find the file and not know where it should be, so it just adds it to the lost+found folder.
In other cases the file's location in the file system tree may still be intact, while the location of all it's data is not (a file can be spread over several places on the disc). In such cases parts of the file would be lost even after recovery, so it's better to place the file somewhere where the user can find it and check it himself instead of just leaving it where it was so that the user have no idea that the file may be corrupted...

---

### Post by eyeJ on 2010-01-17
Jocko thank you for clearing it up! And thanks to Fancypiper for providing the location :D

---

