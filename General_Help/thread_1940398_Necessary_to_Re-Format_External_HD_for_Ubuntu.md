---
title: "Necessary to Re-Format External HD for Ubuntu?"
date: 2012-03-13
forum: General Help
---

### Post by johnsmoke on 2012-03-13
[SIZE=2][COLOR=black]I'm looking to get a 1 to 2 TB portable external HD to store offsite, either Seagate GoFlex or WD Passport. I was wondering, would I be required to reformat either of these drives so that they work with Ubuntu? Just want to make sure prior to making my purchase.[/COLOR][/SIZE]
[SIZE=2][COLOR=black][/COLOR][/SIZE] 
[SIZE=2][COLOR=black]PS-for you fellow Ubuntu users; which is more reliable; the Seagate GoFlex or WD Passport? I'll be using mine to store all my videos and photographs and store them off-site in a safety deposit box.[/COLOR][/SIZE]

---

### Post by Magic Hat on 2012-03-13
I have connected a goflex 2 tb drive right up with no issues and no formatting needed. 

Seagate or Western Digital? They both rank the same in my book.

---

### Post by ajgreeny on 2012-03-13
Linux has no problems reading or writing to ntfs partitions, so there is certainly no need to format the disk, and if there is likely to be a need now, or in the future, for windows to access the drive, it would need to be left as ntfs, which is what I suspect it will be now.

---

### Post by johnsmoke on 2012-03-13
> **Magic Hat said:**
> I have connected a goflex 2 tb drive right up with no issues and no formatting needed. 
 
Seagate or Western Digital? They both rank the same in my book.
 
 
Ok, cool. Yeah, just reading reviews and they vary so greatly that it's hard to make a choice. People have said that they've had Seagates that have failed quickly and vice-versa.... Just hard to make a choice. I want to make it quickly though so that I can begin my massive backup project this weekend!

---

### Post by Mark Phelps on 2012-03-13
Just be aware that some external drives come with Windows software preinstalled -- typically the ones that brag about one-click backup and other such features.

In such a case, you would most likely have to remove the Window software before you could use the drive, but then, it likely would be easier and faster to simply reformat the drive.

---

### Post by johnsmoke on 2012-03-14
> **Mark Phelps said:**
> Just be aware that some external drives come with Windows software preinstalled -- typically the ones that brag about one-click backup and other such features.
 
In such a case, you would most likely have to remove the Window software before you could use the drive, but then, it likely would be easier and faster to simply reformat the drive.
 
 
Yeah, sounds like a good idea. Seems liketh pre-loaded stuff they put on there takes up much un-needed space as well. I'll just re-format when I get the drive, I guess NTFS is the best format to go with at this point, in the chance that I need to access it through a Windows machine (not too probable though). As far as formatting, I guess use Gparted? Or in Ubuntu can you simply right click and select format? 
 
Also, I'm going with the Seagate Goflex 1.5 TB drive. Gives me an extra 500 GB of space as the WD Passport only has 1 TB total.

---

### Post by Helen McCall on 2012-03-18
I wouldn't recommend using an ntfs format for linux. This will not handle filenames or links in the right way. It is far better to reformat with a modern journaling system such as ext3 or ext4. Remember that in the unlikely event of needing to access some files with a windoze machine you can always copy them to a CD/DVD/USB stick.

---

### Post by swright007 on 2012-03-18
I have used Ubuntu Linux for many years and in some computers even dual boot with Windows 7.  All my backup drives, whether they be HD or flash have always been formatted to NTFS or Windows Fat 32 (NTFS works better, I only use regular FAT for boot flash drives).  I have never had an issue with Windows formatted partitions ... with file names or anything else. Ubuntu should see it just fine.  Typical rule of thumb is that Ubuntu can see Windows but Windows can't see Ubuntu.

You can use either "gparted" or Ubuntu's "Disk Utility" .  Check out the differences between the two programs and pick which one works best for you.

---

### Post by mcduck on 2012-03-18
> **Helen McCall said:**
> I wouldn't recommend using an ntfs format for linux. This will not handle filenames or links in the right way. It is far better to reformat with a modern journaling system such as ext3 or ext4. Remember that in the unlikely event of needing to access some files with a windoze machine you can always copy them to a CD/DVD/USB stick.

I pretty much agree with this, at least if you aren't planning on using the drive often with Windows/Mac machines.

Even though using NTFS works reasonably well, using a native Linux filesystem will give you better performance, and also support for file and directory ownership, permissions, symbolic links and other useful features you'd miss if you used a Windows filesystem.

Especially the ownership/permission support can save you from lots of extra work and problems, of course depending on what you plan to use the drive for. (not that the better performance wouldn't be nice as well... ;))

...And on the other hand, if you know you will be using the drive with a Win/Mac system as well, then you'll pretty much have to stick with FAT/NTFS.

---

