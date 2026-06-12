---
title: "Software for accesing files and folders from Ubuntu in another OS"
date: 2010-03-21
forum: General Help
---

### Post by siemprepeligroso on 2010-03-21
Dear firends
I wonder if there is any software that allows full file and folder access from Ubuntu to the Windows XP. In other words Is it possible to access files and folders while being logged on in Ubuntu from another OS like Windows XP

---

### Post by Johnny B on 2010-03-21
Use [Samba]("https://help.ubuntu.com/community/SettingUpSamba")
> Samba is an implementation of the SMB/CIFS protocol for Unix systems, providing support for cross-platform file and printer sharing with Microsoft Windows, OS X, and other Unix systems.


edit: fixed link

---

### Post by Morbius1 on 2010-03-21
Why not try a simple test to find out:

Open Nautilus
Right click on say ... /home/your_user_name/Documents
Select "Sharing Options"
Select all three boxes
Select "Create Share"

Then see if your WinXP box can access the Ubuntu share.

---

### Post by siemprepeligroso on 2010-03-21
OK friends I guess I am misunderstood by you, I was talking about accessing files of WinXP from Ubuntu, but both OS are installed in the same PC (HDD), they are not connected in any kind of network.
am I clear now?

---

### Post by phen0m on 2010-03-21
You should just be able to see the files.  Ubuntu can access NTFS and FAT file systems that Windows uses.

Check what partition your Windows is installed on
```
sudo fdisk -l
```

Check to see if your Windows partition is mounted
```
mount
```

Check out fs-driver if you're looking to see Ubuntu files on XP.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by siemprepeligroso on 2010-03-21
thank you friends, especially phen0m, I will try it a soon as possible and I will write back a feedback, hope it works :)

---

