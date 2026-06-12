---
title: "Convert ext4 file to FAT32"
date: 2011-10-04
forum: General Help
---

### Post by windyrij on 2011-10-04
I need to be able to copy an ext4  file from a Ubuntu desktop system 10.04 LTS to a Windows XP desktop system (FAT32).
( The file in question is a Moneydance data file  - *.md). Is there a simple way to do this?
Thanks   John

---

### Post by nomko on 2011-10-04
What do you mean by an ext4 file?? ext4 is as FAT32 a filesystem, not a file format. Copying from an ext4 file to FAT32 should give you any problems. It's just a mather of copy/paste or cut/paste. Any file on an ext4 drive will not be changed by copying it to a FAT32 disk.
 
Yopu can transfer files from an ext4 disc to any other disc (no matter what the file system is) by means of a cd, dvd or memory stick.

---

### Post by binary00mind on 2011-10-04
> **windyrij said:**
> I need to be able to copy an ext4  file from a Ubuntu desktop system 10.04 LTS to a Windows XP desktop system (FAT32).
( The file in question is a Moneydance data file  - *.md). Is there a simple way to do this?
Thanks   JohnI don't think you have to convert anything. like ext4 to FAT32 
All what you have to do is to rename the file minus the date. 

For example "Moneydance.md" (minus any date(s)). Make a text file with the reference of the date included in the whole name of the *.md file you want to copy. Then you just copy and paste. 

I'm just guessing that there is a date included in your data file that you want to transfer. 

Example: moneydance.md-2011-10-04 change to moneydance.md

---

### Post by dcstar on 2011-10-04
> **binary00mind said:**
> I don't think you have to convert anything. like ext4 to FAT32 
**All what you have to do is to rename the file minus the date.** 
......

Rubbish. Just copy the file.

---

### Post by nomko on 2011-10-04
> **dcstar said:**
> Rubbish. Just copy the file.
 
Just as i mentioned: copy/paste or cut/paste. Files can be transferred by means of a cd or dvd or memory stick.

---

### Post by windyrij on 2011-10-04
Thanks for that, guys. The only other thing I can think of is different versions of Moneydance between the 2 systems.

Thanks, again   John

---

### Post by nomko on 2011-10-04
> **windyrij said:**
> Thanks for that, guys. The only other thing I can think of is different versions of Moneydance between the 2 systems.
 
Thanks, again John
 
Of course there's a difference.... in the architecture of both operating systems. But as it comes to differences between Windows and Linux, Moneydance should work the same way. Both version produce the same file with the same extension. For that there are no differences.

---

### Post by binary00mind on 2011-10-04
> **dcstar said:**
> Rubbish. Just copy the file.The word rubbish was not needed. :neutral:

I came across data files ending with*.md-date.md-date and in this case there are problems with opening the file. 
Sure you can copy anything from any partition regardless NTFS vs FAT vs ext/3/4 or whatever. 
Eureka

---

### Post by windyrij on 2011-10-04
The problem was, as suggested, nothing to do with filesystems, and was a Moneydance issue. The 2008 version (on the Windows system here) cannot open 2011 version files. There is an option in Moneydance 2011 ro export as a 2008 file.

I realise this is not a Ubuntu issue, but mention it in passing. Problem solved!

John

---

