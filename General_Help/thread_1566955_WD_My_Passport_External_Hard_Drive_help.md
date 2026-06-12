---
title: "WD My Passport External Hard Drive help"
date: 2010-09-03
forum: General Help
---

### Post by antturley on 2010-09-03
Hi, 

I'm new to Ubuntu. I love it its spectacular!!!! Just needed to say that. 

My question is: I have a 500gb hard drive from Western Digital or WD (For those searching a similar question on google) My Passport. It was previously formatted to Mac Os x 10.5 blah blah. I have very important data on it  that I need access to. I am running Linux Unbuntu 10.04. The drive is there it hasn't been partitioned all the original smart ware software is still there. I downloaded 'Wine' but no app for it I click on the SmartWare shortcut but it just says application encountered a unexpected error and quits. So can it work? I hope some one out there knows.

Thanks

---

### Post by mastablasta on 2010-09-03
just for anyone googling: you are not asking if the drive can work but if mac file system can work with ubuntu.
 
What does wine have to do with your drive?

---

### Post by jalirious on 2010-09-03
Hi, the software that came on your WD 500 gb passport is junk - use gparted and format it as NTFS so it can be read by both windows and linux and hold files over 4gb.

sudo apt-get gparted ntfsprogs

sudo gparted

Select drive, chose NTFS. Wait till it's done - you're good to go.

---

### Post by mastablasta on 2010-09-03
he needs to access the data on it. formating the disk to different format will erase all that data.

---

### Post by antturley on 2010-09-03
> **mastablasta said:**
> just for anyone googling: you are not asking if the drive can work but if mac file system can work with ubuntu.
 
What does wine have to do with your drive?


Thanks for the quick replies. As I said I am new. I thought wine would be able to load it since it says its reads windows and apple based programs. I am asking if the drive I have that I originally used on a mac, if it can work on linux with out deleting all of my stuff already on it.

---

### Post by antturley on 2010-09-03
Anybody?

---

### Post by mastablasta on 2010-09-03
it seems you need to install hfsplus and hfsutils
 
[http://ubuntuforums.org/showthread.php?t=323105](http://ubuntuforums.org/showthread.php?t=323105)
 
[http://ubuntuforums.org/showthread.php?t=98286](http://ubuntuforums.org/showthread.php?t=98286)
 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1555748](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1555748)
 
----
**Create hfs+ with journaling disabled within Ubuntu **
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1536666](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1536666)

---

### Post by antturley on 2010-09-03
> **mastablasta said:**
> it seems you need to install hfsplus and hfsutils
 
[http://ubuntuforums.org/showthread.php?t=323105](http://ubuntuforums.org/showthread.php?t=323105)
 
[http://ubuntuforums.org/showthread.php?t=98286](http://ubuntuforums.org/showthread.php?t=98286)
 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1555748](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1555748)
 
----
**Create hfs+ with journaling disabled within Ubuntu **
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1536666](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1536666)


Ok so I read the forums you gave me but the file is a .exe for WD. I should have clarified, I was using a mac but now I am running Linux on a pc. The Files for the WD external hard drive shows up on the desktop now but I am still get the same error message. All of the file that use to be .dmg now they are .exe and HFSPlus and HFSSUTILS are now installed but nothing is working. I can't access anything on the drive still.

---

### Post by srs5694 on 2010-09-03
It sounds like the drive may have some sort of weird dual format, which Ubuntu is detecting as NTFS, but with your files stored on a separate HFS+ partition. I suggest you post the output of the following commands, changing /dev/sdb to whatever the drive's ID is:

```

sudo fdisk -lu /dev/sdb
sudo gdisk -l /dev/sdb

```

Note that both commands use a lowercase -L, not a number -1.

Note also that gdisk isn't installed by default; you'll need to install it by typing "sudo apt-get install gdisk" or by downloading it from [its Sourceforge page,](http://sourceforge.net/projects/gptfdisk/files/) which has a much more recent version. I'm suggesting the use of gdisk rather than parted specifically because gdisk probes for the presence of four different types of partition tables, three of which might conceivably be present on the disk.

Also, I concur with jalirious -- don't even attempt to use the WD software that came with the drive, at least under Linux. At best, it will do nothing useful. At worst, it will cause serious problems.

---

### Post by antturley on 2010-09-04
> **srs5694 said:**
> It sounds like the drive may have some sort of weird dual format, which Ubuntu is detecting as NTFS, but with your files stored on a separate HFS+ partition. I suggest you post the output of the following commands, changing /dev/sdb to whatever the drive's ID is:

```

sudo fdisk -lu /dev/sdb
sudo gdisk -l /dev/sdb

```Note that both commands use a lowercase -L, not a number -1.

Note also that gdisk isn't installed by default; you'll need to install it by typing "sudo apt-get install gdisk" or by downloading it from [its Sourceforge page,]("http://sourceforge.net/projects/gptfdisk/files/") which has a much more recent version. I'm suggesting the use of gdisk rather than parted specifically because gdisk probes for the presence of four different types of partition tables, three of which might conceivably be present on the disk.

Also, I concur with jalirious -- don't even attempt to use the WD software that came with the drive, at least under Linux. At best, it will do nothing useful. At worst, it will cause serious problems.

Thanks. I ran into one more little small problem. Once I enter the "sudo fdisk -lu /dev/sdb" for some reason I can't enter the user password into terminal nothing will type at all, I hit enter and type few letters and it tells me its wrong. Am I just doing something wrong?

---

### Post by efflandt on 2010-09-04
Your sudo password is your normal user password.  Nothing appears (no * or anything for characters) when you type an sudo password, you just have to do it blindly.  If you know you entered a wrong character and want to start typing it over, Ctrl+U clears what you typed for the password so far.

---

### Post by antturley on 2010-09-04
Ha I feel special! Thanks. I will give this a try tomorrow gotta get some sleep. If I have any problems (which I'm sure I will) I will be back on again.

---

### Post by coffeecat on 2010-09-04
Just to add to what others have said, this 'Smartware' in WD My Passport drives causes problems in other OSs. Mac users who bought FAT32 My Passport drives and who try to reformat them to hfs+ are tearing their hair out.

From what I can understand, the smartware is on a separate flash drive within the case and this is seen as a separate partition by Linux. Perhaps this is obscuring the main hfs+ HD partition for Linux and perhaps this is why you can't access it. The commands that srs5694 suggested will tell us whether the system can in fact see the hfs+ partition.

A note on hfs+. So long as you can mount the hfs+ partition, you'll be able to access your files. You don't have to install the packages hfsplus and hfsutils first but it doesn't hurt to do so. (I'm posting from a Maverick alpha install without hfsplus and hfsutils and I can access a hfs+ drive just fine.) However there are a couple of things to bear in mind. If the partition is formatted with the default journalled version of hfs+, you won't be able to write to it with Ubuntu, only read it. Ubuntu (Linux) can only write to the non-journalled version of hfs+. Also - depending on how your Mac files were written by your Mac you may run into permissions problems because MacOS (and hfs+) supports the same Unix permissions as Linux and your UID will almost certainly be different between your Mac and Ubuntu

If you do manage to mount the hfs+ partition and you do encounter permissions problems, post back and someone will take you through using 'sudo cp' from the terminal and/or a root Nautilus.

**Edit:** if all this fiddling about trying to access the main partition on the WD drive comes to nothing, I have another suggestion. Can you get hold of a FAT32 USB drive large enough to hold the data you want to copy? Or if not large enough you might be able to do the following in several goes.

Plug both the WD hfs+ drive and the FAT32 drive into your Mac. Copy your files onto the FAT32 drive and then use the FAT32 drive to copy them onto your Ubuntu machine. Both Linux and MacOS can cope with FAT32 just fine. Don't use NTFS because MacOS can only read NTFS (unless you install the Mac version of ntfs-3g). One possible problem if you have any very large video files: the maximum file size in FAT32 is 4GB.

---

### Post by bollucks on 2012-02-02
> **srs5694 said:**
> It sounds like the drive may have some sort of weird dual format, which Ubuntu is detecting as NTFS, but with your files stored on a separate HFS+ partition. I suggest you post the output of the following commands, changing /dev/sdb to whatever the drive's ID is:

```

sudo fdisk -lu /dev/sdb
sudo gdisk -l /dev/sdb

```Note that both commands use a lowercase -L, not a number -1.

Note also that gdisk isn't installed by default; you'll need to install it by typing "sudo apt-get install gdisk" or by downloading it from [its Sourceforge page,]("http://sourceforge.net/projects/gptfdisk/files/") which has a much more recent version. I'm suggesting the use of gdisk rather than parted specifically because gdisk probes for the presence of four different types of partition tables, three of which might conceivably be present on the disk.

Also, I concur with jalirious -- don't even attempt to use the WD software that came with the drive, at least under Linux. At best, it will do nothing useful. At worst, it will cause serious problems.

Thanks for this helpful post. I've installed all suggested: gdisk, hfsplus, hfsutilllll

When I run the commands I get warnings about secondary partitions overlapping and the nowhere can I find a  way to get the data on the hard drive

thanks

---

