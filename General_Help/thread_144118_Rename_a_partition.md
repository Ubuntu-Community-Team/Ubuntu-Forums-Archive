---
title: "Rename a partition"
date: 2006-03-13
forum: General Help
---

### Post by zorkerz on 2006-03-13
Hey there,
I just reformatted an external usb drive useing gparted, with two partitions.  One fat32 and the other ext3.  Now both partitions automount when plugged in but I have no good way of telling them apart.  I would like to be able to rename them so I can tell which is wich.  
Also when booting in windows it recognizes the hardrive, and can see both partitions but does not mount them or give them letters, so i have no way of putting files on them in windows.  Im hopeing this will go away when they are named, or have data on them.
Thanx for the help

---

### Post by Ramses de Norre on 2006-03-13
You can just change the mount point in /etc/fstab to what you want, if you set it under /media/ they will show up at your Desktop.

For windows: download the driver from [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html") and install in windows.

---

### Post by zorkerz on 2006-03-13
Thanx, I have the driver already it works wonderful for my ext3 partition on my internal hardrive, but windows is not mounting the external hardrive at all.  It only shows up in the safley remove hardware area.  More imprtantly the external drive does not have a section in fstab.  I can't just add one can I?  Both partiitons on the external usb drive mount fine and show up on the desktop, I just would like to give them names.

---

### Post by Ramses de Norre on 2006-03-13
They aren't in fstab but they do mount?? How did you do that?
And it's possible the driver for win doesn't support external devices.. I haven't got one myself.. I don't now a solution for know then. (google?:))

---

### Post by RRS on 2006-03-14
Linux newbie/windows amature here, so my ideas on your problem should be approached with caution.

Is it possible that when you created the partitions a new fstab index was created for the USB drive? If so couldn't it be found in the file path after the initial USB mount point? 

SInce I'm only making a guess here I don't know what command you might use to search for it but if my thinking makes sense perhaps someone more knowledgable has a suggestion.

Along the same line of thought the USB drive is probably shown as a single item (either an additional drive letter or simply a USB drive)in "My Computer" in windows and if you click on it it should open to show each partition, though possibly as folders rather then drives. You can verify the device type by right clicking and selecting "Properties".

I'll repeat that I'm only guessing here but if this "theory" seems plausable then hopefully someone with more experience can help you explore it further. I do feel reasonably confident in the windows portion though.

Hope you find an answer as eventually myself and others will probably run into the same problem.

---

### Post by DaBruGo on 2006-03-14
[QUOTE=zorkerz]Hey there,
I just reformatted an external usb drive useing gparted, with two partitions.  One fat32 and the other ext3.  Now both partitions automount when plugged in but I have no good way of telling them apart.  I would like to be able to rename them so I can tell which is wich.  
Also when booting in windows it recognizes the hardrive, and can see both partitions but does not mount them or give them letters, so i have no way of putting files on them in windows.  Im hopeing this will go away when they are named, or have data on them.
Thanx for the help[/QUOTE]

There is an app for windows that will let you see/edit/add files on linux partitions.

Take a look at this [LINK]("http://ubuntuforums.org/showpost.php?p=692413&postcount=171").

Hope it helps.


DAVE

---

### Post by dcstar on 2006-03-14
[QUOTE=zorkerz]Hey there,
I just reformatted an external usb drive useing gparted, with two partitions.  One fat32 and the other ext3.  Now both partitions automount when plugged in but I have no good way of telling them apart.  I would like to be able to rename them so I can tell which is wich.  
.......[/QUOTE]
This should solve most of your problems:

[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)

---

### Post by zorkerz on 2006-03-14
ok i'm am going to clarify my problem a bit just to make sure we are all on the same page.  I've been dual booting between ubuntu and windows for a while now, only useing windows for games and the occasional odd job.  I use my external usb hardrive primarily as backup in case I do something stupid to one of the partitions on the computer.  The hardrive was formatted with a fat32 and an ntfs partitions.  Unfortunatly i don't remember if i partitioned it in windows or ubuntu.  It worked fine in both os', best of all when the two partitions were mounted they had nice names (backup and ntfs).  I've just decided to repartition the hardrive with a fat32 and an ext3 partition useing gparted.  Problem is now that I do not know how to label the partitions on the hardrive itself so they have the same label in both os' and windows does not mount them .  Windows recognizes the hardrive and even that there are two partitions on it but it does not recognize what filesystem either of them are, does not name them, and does not mount them so there seams to be no way to acces them or the data on them.  I do have ext2ifs installed which works great to recognize the ext3 partition on the internal hardrive.  
Fstab:  here i don't know much although i have edited it a little in the past for my internal ntfs partition.  The usb drive is mouunted as sda but nothing is added to the fstab file each time it is plugged in or removed.  Is there somewhere equivalent to fstab for sda drives.  I'm starting to get a little over my head here but thats exciting.  Don't know if this clarifies anything for anyone but myself.  Thanx to all.

---

### Post by zorkerz on 2006-03-15
alright! I found a solution, not very elegant but it works.  My hardrive is made by maxtor, so i used Maxblast 4 to partition the fat32 section of the drive.  This allowed windows to see it and recognize it as a partition.  Next i booted up ubuntu and formated the second section of the drive as ext3 (Maxblast could not do this).  Back in windows i reinstalled ext2ifs which mounted the new partition.  Within windows it is easy to rename partitions simply by right clicking and selecting rename.  Now both partitions are recognized with the correct names in both windows and more importantly Ubunut.  Thanx for the help everyone.  If anybody has a better solution to this please let me know.  I would love to know how to do it entirely within Ubuntu.

---

### Post by chaumurky on 2006-03-16
strange - in an ubuntu install you can name a partition when you format it. What tool is used for that? I guess it's ncurses based bu the looks.

---

### Post by zorkerz on 2006-03-16
[quote=chaumurky]strange - in an ubuntu install you can name a partition when you format it. What tool is used for that? I guess it's ncurses based bu the looks.[/quote]
If you find out what tool actually does this I would love to know
Thanx
elias

---

### Post by DaBruGo on 2006-03-17
[QUOTE=zorkerz]Hey there,
I just reformatted an external usb drive useing gparted, with two partitions.  One fat32 and the other ext3.  Now both partitions automount when plugged in but I have no good way of telling them apart.  I would like to be able to rename them so I can tell which is wich.  
Also when booting in windows it recognizes the hardrive, and can see both partitions but does not mount them or give them letters, so i have no way of putting files on them in windows.  Im hopeing this will go away when they are named, or have data on them.
Thanx for the help[/QUOTE]

zorkerz,

In Windows XP, you can assign a drive letter to your partitions by using the diskmgmt.msc application (start/run/diskmgmt.msc)

Once in there, you can right click on the volume you want to assign a drive letter and then left click on "Change Drive Letter and Paths..." to assign a drive letter to the partitions that Windows will recognize (fat,fat32,ntfs etc.) You can also mount the volume to a folder in XP if you don't want to assign it a drive letter. Or you can do both.

You may even be able to see the linux partitions (as a drive letter) with the "EXT2 IFS" viewer utility you had mentioned, though I have not confirmed this yet.


Hope that helps.

DAVE

---

### Post by DaBruGo on 2006-03-17
[QUOTE=zorkerz]If you find out what tool actually does this I would love to know
Thanx
elias[/QUOTE]

zorkerz,

You can use e2label to label a drive. I believe you can also use a program called tune2fs to label drives. I am not sure if you can format and label at the same time with them though.


DAVE

---

