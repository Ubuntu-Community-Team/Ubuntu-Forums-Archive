---
title: "Windows wont recognize second HDD after Ubuntu Mounted It"
date: 2010-08-22
forum: General Help
---

### Post by mkozlov on 2010-08-22
Ever since I have mounted my secondary HDD with Ubuntu, windows was unable to recognize it at all. This was not a problem before when I used virtualbox as I could map the HDD as a network drive in windows.

Now that I decided to dual boot both operating systems (since virtualbox doesn't perform to my expectations) I am unable to access the secondary HDD with window, which is a real pain.

Ideally I want both OSes to be able to access it with ease, since I will be switching back and forth quite a bit.

---

### Post by lightningfox on 2010-08-22
What filesystem does the second HDD use?

Windows can only read NTFS and FAT filesystem.

To see what fileystem the second HDD uses follow the first part of this webpage: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)


If the filesystem on the second HDD is not NTFS or FAT, you have to format the HDD as NTFS or FAT for Windows to be able to see it.


Before you format it backup any important data on the HDD.

---

### Post by mkozlov on 2010-08-23
Sorry, should have specified. The file system was and is NTFS as this computer used to strictly run windows.

Weird thing is that the drive was labeled as a "dynamic volume" in the windows partition creator while installing Windows XP.

---

