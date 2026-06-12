---
title: "Recovering a formated Hard Drive"
date: 2011-01-23
forum: General Help
---

### Post by sudo101 on 2011-01-23
I wanted to format my Flash USB drive !! and by mistake i choose my external Hard Drive (NTFS) and formated the drive gain to NTFS later when i released that this is not the USB flash drive it was too late to abort or do anything

is there any way to recover my lost data ?! i mean i know about the tools like Recuva ! But the problems that it recover data mixed up in each other

Thanks.

---

### Post by srs5694 on 2011-01-24
I'm not familiar with Recuva, but you could try [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which scans a disk in search of files and recovers them. (Despite its name, it can recover a variety of file types, not just photos.) It won't recover files with their original names, so you'll need to sift through them to identify them. (The Linux "file" command can at least help you identify file types.)

---

### Post by nomko on 2011-01-24
As long you didn't wrote something on that NTFS drive there's a big possibility to rescue a whole lot of data with photorec.
This is very important to know, do not write anything to the disk you want to rescue data from.
At the moment you write data to it, there's a big posibilltiy that you overwrite files that yiou want to rescue.

---

### Post by MarkAlter on 2011-01-24
You must try some data recovery software. try "Kernel for FAT and NTFS" i have personally used this software and it worked like a charm for me. It perfectly recovers data from deleted, formatted, and damaged partitions without errors. One more good thing about this software is you can try free demo version , using demo version you can preview the data recovered before actually buying the software. If you are satisfied with the data preview you can go for buying the software to recover your data.
1. Install the software on ur computer.
2. Connect the external drive to computer. 
3. select the drive(usually G or H for external drive) , click Start. Now the scanning process will start to search the deleted files. After a while you will then get a list of recoverable files.
4. Press Recover to perform full recovery.

---

### Post by Quarkrad on 2011-01-24
Have you a windows environment - dual boot?  I have had a lot of success re this very scenario using a win application called GetDataBack for NTFS.  If your data is very important to you it would be worth creating a partition and putting windows on your pc and installing GetDataBack. You cannot save recovered data to the same partition your querying so if GetDataBack can see files on your external drive you will have to save them to an internal drive. Also - it is very slow (the last time I used it took over 7 hours to scan the formatted drive - 160GB) but in my humble experience it is very good.  Saved me on a number occasions - the only downside it is windows based but it is good.

---

### Post by sudo101 on 2011-01-24
Thanks you all guyz, :) u've been alot of help :)
i've done a scan using couple of application they worked fine to me..
i did like the Active utilities  !! pretty neat stuff...
recovering the files with folders name and file organized in them..

---

