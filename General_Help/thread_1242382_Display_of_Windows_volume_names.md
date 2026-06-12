---
title: "Display of Windows volume names"
date: 2009-08-17
forum: General Help
---

### Post by Howard Kaikow on 2009-08-17
Why does Ubuntu display Windows volume names differently than does My Computer in Windows 2000?

Yesterday, I got the urge to change the volume name for each of my 11 internal partitions to use only lower case. 10 drives are NTFS, the other is FAT32. Guess which is misbehaving?

My Computer, in Windows correctly displays all 11 as all lower case, tho certain apps continue to display upper case for the FAT 32 partition.

Booting to Ubuntu 9.04, Computer displays 10 in lower case, but the FAT32 partition as upper case.

Why would My Computer, in Windows, and Computer, in ubuntu, display the FAT32 volume name differently?

Ubuntu's partition manager allowed me to change the name to lower case, but as soon as I exited the partition manager, the displayed name reverted to upper case.

Page 1515 of the Windows 2000 Pro Resouce Kit states there is an 11 byte field named Volume Label in the Extended BPB for a FAT32 volume.

The description of the field is "A field one used to store the volue label. The volume label is now stored as a special file in the root directory.". As far as I can tell, that file is not visible via the GUI.

---

### Post by hephaeastus on 2009-11-01
I also have this problem and I find it very annoying :sad:, because I use LaTeX and have to define pathnames within my code for images. I would greatly appreciate a reply to this.

Thanks.

---Hephaeastus

---

