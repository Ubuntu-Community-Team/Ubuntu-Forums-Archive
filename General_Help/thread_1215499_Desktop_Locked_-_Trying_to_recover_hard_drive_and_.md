---
title: "Desktop Locked - Trying to recover hard drive and reload OS"
date: 2009-07-17
forum: General Help
---

### Post by Element116 on 2009-07-17
[FONT=Helv][SIZE=2]
[SIZE=2][FONT=Helv]My mom's Ubuntu PC locks up (cursor will not move) once the desktop loads. I tried this with no luck...[/FONT][/SIZE]
 
[SIZE=2][FONT=Helv][http://ubuntu-unleashed.com/2008/05/howto-restart-ubuntu-linux-safely-when-it-is-frozen-or-locked-up.html](http://ubuntu-unleashed.com/2008/05/howto-restart-ubuntu-linux-safely-when-it-is-frozen-or-locked-up.html)[/FONT][/SIZE]
 
[SIZE=2][FONT=Helv][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]I'm a complete stranger to this OS, so I figured that I would just pull the hard drive, slide it into my Windows PC and pull the data off it so I could reformat it and either reload Ubuntu or just put Windows onto it for her. For some reason, the hard drive is found when I hook it up to my PC, but I cannot assign a drive letter (the option is greyed out). Is there any reason that Ubuntu could be causing this (i.e., Windows can't recognize a hard drive with Ubuntu on it?). Seems strange to me, but I'm stumped. I set the drive to slave before I installed it so I didn't miss that part of it. I have no problems reading other hard drives that I formatted on my PC ( I have a spare one that I popped in just to try it out). Appreciate any insight either getting access to the hard drive or fixing Ubuntu. Thanks.[/SIZE][/FONT]
[/SIZE][/FONT][/FONT][/SIZE][/SIZE][/FONT]

---

### Post by itsjareds on 2009-07-17
Ubuntu's filesystem is different from Windows's, so Windows does not know how to read it. There are some free tools that would let you read Ubuntu's partition, but I don't think you'll need it. You're just going to reformat it, anyways.

If you know how to format partitions from Windows, IIRC you should be able to see the Ubuntu partition from the Windows formatter.

---

### Post by Element116 on 2009-07-17
Thanks. In Windows, I see 3 or 4 partitions on the drive IIRC. The problem is that none of them are readible. I was hoping to access the files she has in order to copy them over to one of my hard drives. She has a lot of photos hat she doesn't want to lose. I'll look into the free tools you mentioned since that may be my best bet before I reformat the drive.

---

### Post by itsjareds on 2009-07-17
Does your mom still have the Ubuntu LiveCD (the install disc)? If she does, you should be able too boot into that and copy your files from your Ubuntu partition onto your Windows one. You can even reformat your Ubuntu partition from the CD after you copy her stuff. To reformat from the LiveCD, go to System > Administration > Partition editor.

If you're going to re-install Ubuntu, format it to ext3, if you're putting Windows on it, format to NTFS.

---

### Post by Element116 on 2009-07-17
Thanks. I need to check on the CD. I assume so unless she misplaced it. I'm not sure there is a Window's partition on her hard drive. I don't recall seeing any listed as NTFS which is why I believe my windows PC could not recognize it... I'll re-check as it's been a week or so since I last looked at it.

---

### Post by louieb on 2009-07-17
[Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")
[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") 

Assuming you did a standard install you should be able to use one of these to see the Linux partitions in windows and get the data off.

---

### Post by itsjareds on 2009-07-17
> **Element116 said:**
> Thanks. I need to check on the CD. I assume so unless she misplaced it. I'm not sure there is a Window's partition on her hard drive. I don't recall seeing any listed as NTFS which is why I believe my windows PC could not recognize it... I'll re-check as it's been a week or so since I last looked at it.

Oh sorry, I think I got you mixed up with another thread similar to this one :P

Either way, the steps are the same. Have you found the Ubuntu LiveCD? This is preferred over a GParted CD because we can also manage your files with the Ubuntu CD. GParted has a terminal that you can do some stuff with, but it's much more difficult to use than copying files with the file manager.

If you're using the Ubuntu CD:
1. Both drives should be seen by your computer. Copying the files from your mom's hard drive over to yours should be trivial.
2. Format the Ubuntu drive to either NTFS or ext3, based on what OS you want to install on it. This will clear all data.
3. Now you're free to install whatever OS you want on it. Just follow the steps on whatever install CD you use.

Tell me if you're using the GParted CD, it's a little more complex to copy files.

An alternative to using Linux to copy files is to use a Windows ext2/ext3 driver, but I thought you were just reformatting so I didn't suggest it. I've been very happy using Ext2FSD, it's a program that lets you mount ext2/ext3 filesystems on Windows and give them a drive letter.

Here's a download link of the latest version's installer (exe):
[http://prdownloads.sourceforge.net/ext2fsd/Ext2Fsd-0.46.exe?download]("http://prdownloads.sourceforge.net/ext2fsd/Ext2Fsd-0.46.exe?download")

More information about Ext2fsd at this page:
[http://ext2fsd.sourceforge.net/projects/projects.htm]("http://ext2fsd.sourceforge.net/projects/projects.htm")

---

### Post by Element116 on 2009-07-17
Awesome. Thanks to both of you for the info. I'll get on it this weekend and report back.

---

