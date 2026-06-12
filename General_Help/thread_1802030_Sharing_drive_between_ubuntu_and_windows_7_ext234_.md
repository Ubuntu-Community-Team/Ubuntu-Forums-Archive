---
title: "Sharing drive between ubuntu and windows 7: ext2/3/4 or NTFS?"
date: 2011-07-11
forum: General Help
---

### Post by quickk on 2011-07-11
Hi everyone, 

    I want to share a media drive between Windows 7 and Ubuntu 11.04.   This drive will hold all of my pictures so that I can edit them in Windows with Photoshop.   

What is my best bet?

A) Format the drive as NTFS.   Are there any problems that I should be aware of with NTFS in Ubuntu?   

B) Format the drive as ext2, use [Ext2Fsd]("http://www.ext2fsd.com/") to use it in windows?  Will this be seamless? 

C) Use ext3 + Ext2Fsd.   I know that there might be problems with ext4, but does ext3 work seamlessly in windows 7?

Thanks!

---

### Post by 3Miro on 2011-07-11
I used to share NTFS drive between Ubuntu and Windows and that was back in 8.04. I had no issues.

I think Windows 7 has some issues if Ubuntu is writing to its main partition (i.e. C:\ with the installation), but there should be no problems with an extra partition.

---

### Post by quickk on 2011-07-11
Thanks!  I just want this to be as seamless as possible so that my drive shows up automatically in both windows and linux, and that I don't have to worry about data loss, etc.

With NTFS, do I have to worry about permissions?   If the computer looses its power suddenly, do I have to worry about the NTFS drive?

---

### Post by 3Miro on 2011-07-11
> **quickk said:**
> Thanks!  I just want this to be as seamless as possible so that my drive shows up automatically in both windows and linux, and that I don't have to worry about data loss, etc.

Sounds like NTFS is your best bet. I have never had trouble with Ubuntu not recognizing an NTFS drive.

---

### Post by quickk on 2011-07-11
One last question: are there differences in allowed file names between NTFS and ext?   For example, can I have a file name like author:year.pdf in NTFS?

Scratch that.  That was a dumb question since I want my file names to be compatible with Windows too.

---

### Post by Jouke74 on 2011-07-11
NTFS seems to be the most stable, also since Windows can easily fix any issues with the file system in case of problems. Running Ext2-3 (not ext4) under Windows is possible but more tricky (it is a choice since Ubuntu can be used to recover files in case of issues). 

An issue is indeed the long file names using multiple points: a name like part1.part.part3.part4.part5 might cause issues, usually not when reading the file, but more when copying, or moving the file to trash. Of course, this can always be done under the OS where the files was originally made.

---

### Post by quickk on 2011-07-25
One unanticipated side-effect of using NTFS was that I had lots of difficulty sharing the drive with other windows machines via samba.   Windows kept complaining that it could not see the shares even though they were listed.  

It turns out that this is due to the fact that file permissions on an ntfs drive have to be set upon mounting.  Once I correctly updated my fstab, then I could share the drive without any [problems]("http://ubuntuforums.org/showthread.php?t=1811536"). 

Actually, I may of had to enter:

user: anonymous
password: 

(password was left blank)

on the windows side, but then it worked fine.

---

### Post by ToshibaLaptoplinux on 2012-03-13
[http://ubuntuforums.org/showthread.php?t=1940122]("http://ubuntuforums.org/showthread.php?t=1940122")

---

