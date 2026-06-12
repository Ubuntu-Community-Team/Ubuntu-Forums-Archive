---
title: "Harddrive Renaming Problem"
date: 2010-01-09
forum: General Help
---

### Post by joelandsonja on 2010-01-09
Alright, I searched the forums to find this problem, but I was not successful. 

I have been trying to rename my harddrives in Gparted, but whenever I try to Unmount the drives (so I am able to select the 'label' command) it gives me an error message in the form of the Exclamation mark icon instead of the Keys icon. When I read the information for the drive after I see the error message displayed it says "Unable to read the contents of this file system. Because of this, some operations may be unavailable."

Any thoughts on how to fix this problem?

---

### Post by lyall on 2010-01-09
> **joelandsonja said:**
> Alright, I searched the forums to find this problem, but I was not successful. 

I have been trying to rename my harddrives in Gparted, but whenever I try to Unmount the drives (so I am able to select the 'label' command) it gives me an error message in the form of the Exclamation mark icon instead of the Keys icon. When I read the information for the drive after I see the error message displayed it says "Unable to read the contents of this file system. Because of this, some operations may be unavailable."

Any thoughts on how to fix this problem?

I hope I can help

are you trying to to rename a second hard drive?
You should be able to in Gparted.  I was able too.

to rename the first hard drive that has Ubuntu installed on it I do not think you can.  Unmounting your Ubuntu drive you would not be able to communicate to it.
You might if you have a bootable CD with Gparted on it, because you are not using that drive.
see gparted web site on how to made a bootable CD or USB
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

good luck and have fun learning

---

### Post by 73ckn797 on 2010-01-09
> **lyall said:**
> I hope I can help

are you trying to to rename a second hard drive?
You should be able to in Gparted.  I was able too.

to rename the first hard drive that has Ubuntu installed on it I do not think you can.  Unmounting your Ubuntu drive you would not be able to communicate to it.
You might if you have a bootable CD with Gparted on it, because you are not using that drive.
see gparted web site on how to made a bootable CD or USB
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

good luck and have fun learning


+1

Boot from the LiveCD and you can accomplish what you are wanting via gparted.

---

### Post by kman269 on 2010-01-09
What's the file system? it may not be supported by gparted or you may need something extra to make it supported.

---

### Post by joelandsonja on 2010-01-10
I am trying to rename 4 separate external harddrives. They only have video files on them, and should in theory rename in Gparted. I was actually able to rename one of the harddrives before I had this problem, but now it doesn't want to work.

---

### Post by joelandsonja on 2010-01-10
Any other suggestions? 

I am breaking my head trying to come up with a solution, but nothing seems to work.

---

### Post by michy99 on 2010-01-10
If you are running 9.10, try labeling them in System->Administration->Disk Utility.

---

### Post by nothingspecial on 2010-01-10
Again, what file system are they?


ntfs, fat32, ext3 ........????????

---

### Post by joelandsonja on 2010-01-10
Most file systems are NFTS and I have one that is FAT32

---

### Post by sgosnell on 2010-01-10
Do you have the ntfs extensions installed?

---

### Post by joelandsonja on 2010-01-10
Alright, I figured it out ... sadly Ubuntu was needlessly complicated because I simply reinstalled Windows and rightclicked on the harddrives and renamed it.

It should be that easy on Ubuntu ... :(

---

### Post by scouser73 on 2010-01-10
[[COLOR="Red"]**Ubuntu: Rename Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by Leppie on 2010-01-10
> **joelandsonja said:**
> Alright, I figured it out ... sadly Ubuntu was needlessly complicated because I simply reinstalled Windows and rightclicked on the harddrives and renamed it.

It should be that easy on Ubuntu ... :(

i think you forgot to add yourself to the fuse group (which allows you to mount and unmount):
```
sudo adduser <yourusername> fuse
```

---

### Post by warfacegod on 2010-01-10
> **joelandsonja said:**
> Alright, I figured it out ... sadly Ubuntu was needlessly complicated because I simply reinstalled Windows and rightclicked on the harddrives and renamed it.

It should be that easy on Ubuntu ... :(

Your drives were formatted with Windows owned file systems. Legally, Ubuntu can't install itself knowing how to write to them. You need to add that ability yourself. Search Synaptic Package Manager for ntfs. There should be two or three items to check to fix this. Read the descriptions to make sure you get the proper ones.

---

### Post by joelandsonja on 2010-01-12
I am not sure, how do I do that?

---

### Post by Leppie on 2010-01-12
you can add ntfsprogs for advanced ntfs support, dosfstools for fat:
```
sudo apt-get install ntfsprogs dosfstools
```
you should then be able to use these extra's in gparted.

---

### Post by warfacegod on 2010-01-12
If you aren't comfortable with the Terminal, you ca find them in: System> Admin.> Synaptic Package Manager.

---

### Post by joelandsonja on 2010-01-12
Alright, it seemed to work, but I'm not sure why.

I'll settle this thread as solved, but I'm not entirely sure what solved it. I downloaded the files you all suggested, but I was only able to rename the harddrives through Gparted. (Which wasn't working originally) 

At any rate, thanks for the help!

---

### Post by warfacegod on 2010-01-12
> **joelandsonja said:**
> Alright, it seemed to work, but I'm not sure why.

I'll settle this thread as solved, but I'm not entirely sure what solved it. I downloaded the files you all suggested, but I was only able to rename the harddrives through Gparted. (Which wasn't working originally) 

At any rate, thanks for the help!

Because, as I said before, Ubuntu cannot legally write to a NTFS drive when it is installed. You must add that ability yourself (which is not illegal) and you now have done that. Therefor, you now have the ability to change the drive name and the name itself resides on the drive.

---

### Post by michy99 on 2010-01-12
I'm pretty sure that all recent Ununtu versions come with ntfs support already installed.

---

### Post by warfacegod on 2010-01-12
> **michy99 said:**
> I'm pretty sure that all recent Ununtu versions come with ntfs support already installed.

My 9.04 and 9.10 both were unable to write to NTFS "out of the box". Neither was my wife's 8.10, 9.04, or 9.10, all fresh installs on three different machines.

---

### Post by michy99 on 2010-01-12
You may be right. I told the installer to mount my ntfs partition when I was installing, so it probably installed the ntfs packages at that point. I know that I didn't have to manually install them.

---

