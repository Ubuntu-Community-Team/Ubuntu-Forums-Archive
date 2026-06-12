---
title: "Unable to create new folder on external USB drives"
date: 2010-10-01
forum: General Help
---

### Post by rmcellig on 2010-10-01
I have some USB drives that for some reason I cannot create folders or documents on. This pertains to all of my external USB drives. Works fine when I am in the Mac partition but not in Ubuntu. Another thing is that when I plug in an external drive, a nautilus window with the contents of the drive opens. Happens to all of my USB drives. How can I fix these problems?

---

### Post by mörgæs on 2010-10-02
> **rmcellig said:**
> I have some USB drives that for some reason I cannot create folders or documents on. This pertains to all of my external USB drives. Works fine when I am in the Mac partition but not in Ubuntu. 

It sounds like missing user rights. Can you create a file with sudo?

> **rmcellig said:**
> Another thing is that when I plug in an external drive, a  nautilus window with the contents of the drive opens. Happens to all of  my USB drives. How can I fix these problems?

My guess is that this is intended.

---

### Post by garvinrick4 on 2010-10-02
> **rmcellig said:**
> I have some USB drives that for some reason I cannot create folders or documents on. This pertains to all of my external USB drives. Works fine when I am in the Mac partition but not in Ubuntu. Another thing is that when I plug in an external drive, a nautilus window with the contents of the drive opens. Happens to all of my USB drives. How can I fix these problems?
Go to configuration editor and to apps to nautilus to preferences and choose to mount or open or both.

Have you tried to make a new folder while in root.
Alt/F2 type in gksudo nautilus open usb drive right click and make folder. Have USB mounted.

Check permissions on drives.
cd /media
ls -la

---

### Post by rmcellig on 2010-10-02
These are the permisssions:

drwxr-xr-x 14 root  root   4096 2010-10-02 07:12 .
drwxr-xr-x 22 root  root   4096 2010-10-01 18:47 ..
drwxrwxr-t  1 root     80    36 2010-10-01 21:16 HD09
drwxrwxr-x  1    99    99    28 2010-09-20 09:59 HD1
drwxrwxr-x  1    99    99   103 2010-09-28 15:53 HD13
drwxrwxr-x  1    99    99    19 2010-09-18 21:26 HD2
drwxrwxr-x  1    99    99    31 2010-09-20 13:44 HD3
drwxrwxr-x  1    99    99    44 2010-09-21 15:05 HD5
drwxrwxr-x  1    99    99    21 2010-09-15 17:12 HD6
drwxrwxr-x  1    99    99    46 2010-09-18 17:32 HD8
drwxrwxr-x  1    99    99    48 2010-09-25 09:17 Media
drwx------ 15 randy randy 32768 1969-12-31 19:00 RADIO1
drwx------ 18 randy randy 32768 1969-12-31 19:00 RADIO2
drwxrwxr-x  1    99    99    11 2010-09-23 07:36 timemachine


Where do I go from here?

I tried opening the drives in root and I still can't create folders.

---

### Post by coffeecat on 2010-10-02
This:

> **rmcellig said:**
> drwxrwxr-x  1    99    99    11 2010-09-23 07:36 timemachine


... suggests you are using this drive on your Mac for TimeMachine backups. Is that correct? Because, if so, it's almost certainly formatted with the MacOS filesystem hfs+. And if that's the journalled version of hfs+, Linux cannot write to it. Did you format the drive in the Mac Disk Utility app? If you did and it's formatted journalled hfs+ then you won't be able to save a file on it from Ubuntu, let alone create a folder.

---

### Post by rmcellig on 2010-10-02
My Radio1 and radio2 drives work fine. I can create folders. These drives are formatted Windows which Ubuntu can read/write to. So there is no way at all short of reformatting the drives to Windows format? These drives have a lot of stuff on them. I guess I can do that as I have some other USB drives I can temporaily put the files on. Bottom line is that I would like all the USB drives to be able to read/write on the Mac, PC and Linux. With FAT 32 formatting there is the 4GB file size limit I think. What about NTFS. Can all three platforms read/write to this format?

Please advise and thanks for the info. I should have known bette regarding HFS+.

---

### Post by coffeecat on 2010-10-02
> **rmcellig said:**
> What about NTFS. Can all three platforms read/write to this format?

Yes, if you install the ntfs-3g driver in MacOS. But that is slow.

Here's a thread where I covered these points - at least as far as I understand them. There's a bit about partition tables as well, but the pros and cons of various filesystems for Mac/Windows/Linux sharing is discussed.

[http://ubuntuforums.org/showthread.php?t=1574467](http://ubuntuforums.org/showthread.php?t=1574467)

If you are using Time Machine you won't be able to do backups onto NTFS or FAT32. Microsoft filesystems don't support Unix permissions which both Mac and Linux need.

---

### Post by rmcellig on 2010-10-02
Right now Time Machine is a partition of one of the drives. I think I will dedicate an entire drive formatted HFS+ to it. I think that is better. As far as the other drives are concerned, I guess that Fat32 is my only option for all the drives except the time machine one. I can do everything in my Ubuntu partition regarding formatting or my Mac.

---

