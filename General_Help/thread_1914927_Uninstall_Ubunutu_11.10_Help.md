---
title: "Uninstall Ubunutu 11.10 Help"
date: 2012-01-25
forum: General Help
---

### Post by user127 on 2012-01-25
I installed ubuntu while using the desktop verson of 11.10.  Even though I clicked install along side of windows, it erased windows.  I reinstalled windows and it wont let me boot ubuntu now.  Is there any way i can uninstall or erase ubuntu from my computer because it is taking up 30GB of space?

---

### Post by Mark Phelps on 2012-01-25
You didn't say which version of MS Windows you're running -- but if you're using Win7, open the Win7 Disk Management utility and delete the partition (MS calls them "drives") that contains Ubuntu.

You can then use the same utility to either create a new NTFS partition in the free space, or expand an existing partition to fill that space.

---

### Post by raja.genupula on 2012-01-25
I agree with Mark Phelps , But when i am managing my system with Windows and Ubuntu (long back ago and at that time xp i am using).When i did like that some times my other partitions are also getting disturbed . 

so what i suggest is put live cd/USB of Ubuntu and run a live session and from that delete that partition which you wanna format , make it as free space.

then follow as Mark Phelps said .

All the best .

---

### Post by user127 on 2012-01-29
Im using Windows vista.  Will that make a difference?
I think I already tried that and it didnt work.
I might have put it in C instead of making it in a different partition.

---

### Post by Bucky Ball on 2012-01-29
I am unaware MS Windows of any description will know what an EXT* partition is and be capable of deleting it. I would slip in the LiveCD, 'Try Ubuntu', open Gparted and delete the Ubuntu partition.

---

### Post by user127 on 2012-01-29
I don't think I made a separate Ubuntu partition.  I think i just put it on C, by accident

---

### Post by Bucky Ball on 2012-01-29
So this is a Wubi install, not a complete install to the hard drive? Bit confused. A wubi install couldn't wipe windows but your install did. You then installed Windows again but Ubuntu is still there ...

This would indicate Windows and Ubuntu are on separate partitions.

---

### Post by user127 on 2012-01-29
no its not Wubi but it did erase windows

---

### Post by Bucky Ball on 2012-01-30
So you have them on separate partitions, then. Either way refer to post #5. The Ubuntu partition will be displayed and recognised as an EXT partition, either EXT4 or EXT3. Windows, if it's there, will be NTFS. Kill the EXT partition(s).

---

### Post by mastablasta on 2012-01-30
> **Bucky Ball said:**
> I am unaware MS Windows of any description will know what an EXT* partition is and be capable of deleting it. I would slip in the LiveCD, 'Try Ubuntu', open Gparted and delete the Ubuntu partition.
 
it does see it as unformated disk space. it can also delete the partitions or reformat them to NTFS.
 
Windows can also read ext partition but special tools are needed for that.

---

