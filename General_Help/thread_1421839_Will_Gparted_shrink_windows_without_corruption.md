---
title: "Will Gparted shrink windows without corruption?"
date: 2010-03-04
forum: General Help
---

### Post by jeremyleroy96 on 2010-03-04
I want to use gparted to extend my ubuntu partition but when i boot into windows i can't shrink it anymore because system files at the end of the volume! So will gparted move the files correctly or will it corrupt my windows? Its windows 7 if that effects anything

---

### Post by louieb on 2010-03-04
It should but there is no guarantee. 

Most of the time on the 1st reboot after using Gparted - windows will want to run chkdsk - let it run and let it finish.     

Note: For Vista and Win7  - If you use Gparted then make sure the box align to cylinder boundary is not checked.

---

### Post by jeremyleroy96 on 2010-03-04
by it should you mean it won't corrupt right? Well its worth a shot i guess. I might just get rid of win 7 beta and put vista back on it so if it screws up not a huge deal

---

### Post by lisati on 2010-03-04
It *should* be able to do it. Deleting temporary files (see sig), defragging and making backups first is always a good idea, "just in case". Some people find turning off indexing and system restore can sometimes free up a bit of space otherwise taken up by system files.

---

### Post by todd2982 on 2010-03-04
Windows 7 has a built in partition manager that will shrink and grow it's own partitions. It has worked great for me and I don't have to boot into anything special.

Just back up your stuff anytime you change your partitions.

---

### Post by MooPi on 2010-03-04
I don't believe Gparted is capable of shrinking ntfs file systems. You're going to need to use the utility suite ntfsprogs to do the job. At least that has been what I've used recently. 
Correction
> I just checked the Gparted FAQ page and it states that gparted can resize ntfs. It would not work for me and I did use ntfsresize to do the job.

---

### Post by ndefontenay on 2010-03-04
I do that in windows too. I went to Administrators Tools>Computer management> Disk management and shrink-ed my single huge partition. It would shrink only to half size because of system files :/

I don't mind though. I use my ntfs partition as a backup partition. That way I can save stuff there and use it in linux when I need it. After all, I re-install windows never, and I re-install ubuntu quite often to see how new releases go.

---

### Post by louieb on 2010-03-04
I've used Gparted several times to resize partitions with the Microsoft NTFS file-system. Think it was the 1st or 2nd time I used it  - when finished - widows (XP) refused to boot. I tried some of the widows repair tools - but never got the OS to boot.   Maybe it was just my inexperience. Anyway since I had my data copied off on another drive. Just when ahead and did a reinstall.   

I still use Gparted for all my partition needs -  other than the one time I've not had any problems with it since.

---

### Post by jeremyleroy96 on 2010-03-05
I said above that i can not shrink the volume anymore in windows. I wanted to use GParted but i don't want it to be corrupted (of course)

---

### Post by CongoJim on 2010-03-05
Windows 7 can't shrink further because it has placed "immovable" files at the end of the partition. There is a third party program that moves the immovable for you then windows can do the shrinking without fear. I don't have the program at my fingertips but I'd google it if I were you before trying anything else just to be safe.

---

### Post by Mark Phelps on 2010-03-05
> **jeremyleroy96 said:**
> I said above that i can not shrink the volume anymore in windows. I wanted to use GParted but i don't want it to be corrupted (of course)

Before you do anything else, use the backup feature in Win7 to create and burn a Win7 Repair CD.  That way, if GParted does corrupt your OS, you can boot using that CD and repair it.

As to shrinkage, it's generally a bad idea to use GParted to shrink the Vista/Win7 OS partition more than Windows permits.  If you check the link below, it has some tips on things you can do to possibly get more shrinkage out of the Disk Management utility:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by tom4jean on 2010-03-05
Use the windows 7 volume manager from within windows to shrink windows 7, not G parted. It is very easy to do.

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

And once you do reboot a few times to be sure the MBR in windows adjusts itself to the new volume size prior to installing anything on the new empty space.
I just did two computers this way and then installed ubuntu dual boot with no problem and windows was fine.

See and follow this well written guide it tells you exactly what to do..

It works very well, If you are looking to dual boot I would also recommend following the guide below and using easyBCD as the guide says under the MBR section, but you need the beta 2.0 version of easyBCD for grub 2. search the forum on the esaybcd site for it.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by carlosgs91 on 2010-03-05
.

---

### Post by sgage on 2010-03-05
I have used gparted to shrink an ntfs partition beyond what Windows would let me do. It has worked for me. Definitely let Windows do a chkdsk afterwards, though.

---

### Post by dcstar on 2010-03-06
> **sgage said:**
> I have used gparted to shrink an ntfs partition beyond what Windows would let me do. It has worked for me. Definitely let Windows do a chkdsk afterwards, though.

I have also found that it is good policy to do a Windows Defrag before using Gparted to shrink the partition, it seems to make the process quicker.

---

### Post by uRock on 2010-03-06
> **jeremyleroy96 said:**
> I want to use gparted to extend my ubuntu partition but when i boot into windows i can't shrink it anymore because system files at the end of the volume! So will gparted move the files correctly or will it corrupt my windows? Its windows 7 if that effects anything

Go into your start menu and find the selection to make backups and such. Burn a copy of the repair disk. You may need this disk after altering the partitions.

---

