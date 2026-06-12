---
title: "How to successfully copy files greater than 9 gig to external hard drive?"
date: 2009-09-28
forum: General Help
---

### Post by kazuya on 2009-09-28
Hey guys. For a week now I have been having difficulty with trying to copy a file greater than 9 gig to external hard drive? The file executable or exe file is 9.12 gig. I downloaded it to my windows partition(VISTA crud) and I am trying to copy it from there to my 750 gig external hard drive.

I tried to copy the zip file or the extracted file as user and as root to the external hard drive which is NTFS formated i believe. Will I have better luck with FAT 32?

Does anyone know how to copy a 9 gig executable file to an external hard drive.?

Or is it possibleto download the 9 gig file straight into the external hard drive?

I am connected via USB. 

Any ideas?

---

### Post by gordintoronto on 2009-09-28
FAT32 has a maximum file size of 4 GB, so that's not a solution.  NTFS should be able to handle your file.

---

### Post by kazuya on 2009-09-28
Thanks man. I think that external harddrive was partitioned in FAT32. Is it possible for me to resize it and have parts of the partition reformatted as NTFS without losing the data on FAT32 part of external hard drive?

---

### Post by gordintoronto on 2009-09-28
> **kazuya said:**
> Thanks man. I think that external harddrive was partitioned in FAT32. Is it possible for me to resize it and have parts of the partition reformatted as NTFS without losing the data on FAT32 part of external hard drive?

I don't know.

---

### Post by blackened on 2009-09-28
> **kazuya said:**
> Thanks man. I think that external harddrive was partitioned in FAT32. Is it possible for me to resize it and have parts of the partition reformatted as NTFS without losing the data on FAT32 part of external hard drive?

No, it's not possible for one partition to use two different filesystem types.

The solution is to use something like gparted to shrink the FAT32 partition, then create an NTFS partition in the unallocated space.

After that you should be able to save your file to the NTFS partition with no issues.

---

### Post by Darkwing-Duck on 2009-09-29
Okay, I did some digging on this and I cannot find a way to do it in Linux. However. If you have a friend/family member who still uses windows there is a way to do it.

This site was VERY helpful when I did it with my 750gig drive on my brothers XP laptop.

[http://www.partition-tool.com/resource/convert-file-system-from-fat32-to-ntfs.htm](http://www.partition-tool.com/resource/convert-file-system-from-fat32-to-ntfs.htm)

It is using a program called EASEUS Partition tool ([http://www.partition-tool.com/](http://www.partition-tool.com/)) and what it does is partition a little at a time and copy your files over at the same time. As it makes room it continues the partition. For those programmers out there this would be a great idea to check into.

Hope this helps at least a little.

---

### Post by stinger30au on 2009-09-29
what u could do is make a copy of the original file

take the copy of the file and cut it in to smaller slices and move it to the hdd then join it

you can do this from command line or use winrar and rar the file and tell it what size to make the file sizes

i just did a qucik google and found this on how to use split and join for you

[http://www.ubuntu-inside.me/2009/02/how-to-join-and-split-files-under.html](http://www.ubuntu-inside.me/2009/02/how-to-join-and-split-files-under.html)

---

### Post by stinger30au on 2009-09-29
[http://www.izarc.org/](http://www.izarc.org/)


you could do it for free with izarc if you dont like winrar

---

### Post by P4man on 2009-09-29
> **kazuya said:**
> Thanks man. I think that external harddrive was partitioned in FAT32. Is it possible for me to resize it and have parts of the partition reformatted as NTFS without losing the data on FAT32 part of external hard drive?

Yes, you can do that in windows. There is command in windows to do just that. (convert.exe) **However,** if you intend to use that drive with Ubuntu, you should NOT do that. A Fat32->ntfs converted volume has some limitations compared to a volume that was "natively" formatted as ntfs, (think it has to do with cluster size, but Im not sure), and ubuntu will choke on such volumes giving you abnormal slow writing speed. I mean 10x to 100x slower  than a normally formatted ntfs volume.

---

