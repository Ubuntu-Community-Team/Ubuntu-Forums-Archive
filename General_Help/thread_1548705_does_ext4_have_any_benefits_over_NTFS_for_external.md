---
title: "does ext4 have any benefits over NTFS for external HDDs?"
date: 2010-08-08
forum: General Help
---

### Post by lue42x on 2010-08-08
I have a new external harddrive (usb 2.0, 500gb) and I would like to use it with my Ubuntu laptop.  I don't intend on using it with other OSes so compatibility isn't really an issue.  The external drive is currently FAT32. I've heard this file system isn't as good as NTFS or ext4 (ext4 is what Ubuntu 10.04 uses right?) so I want to change the file system to either NTFS or ext4.

Are there any important advantages/disadvantages I should think about before formatting the drive?

---

### Post by mike555 on 2010-08-08
Fat and ntfs gets fragmented , ext3 or 4 doesn't (well not noticeably )

---

### Post by Lolo Uila on 2010-08-08
Unless something has changed that I'm not aware of, I don't believe Linux fully supports NTFS journaling (only partial support). I don't believe it supports NTFS encryption either.

If you have no need for MS compatibility I see no reason to use a non-native file system.

With a native file system you will have access to all the features supported by that file system, and a native file system will be better optimized for performance. Go with ext4.

---

### Post by lue42x on 2010-08-08
Cool, thanks guys.

I do have one hypothetical question though.  If I one day want to copy data from a thumb drive or external hdd that uses FAT32 or NTFS to my new external that will use ext4, that will be okay right?  Or will that cause the fragmenting of that data on the new ext4 HDD?

---

### Post by linux18 on 2010-08-08
> **lue42x said:**
> Cool, thanks guys.

I do have one hypothetical question though.  If I one day want to copy data from a thumb drive or external hdd that uses FAT32 or NTFS to my new external that will use ext4, that will be okay right?  Or will that cause the fragmenting of that data on the new ext4 HDD?
no, it wont fragment your new drive
try xfs its even faster than ext4

---

### Post by ed-koala on 2010-08-08
Nope, no problems.

If you ever plan to take your external drive to someone else's place who might run Windows, you may want to keep it as NTFS as MS doesn't "see" ext3 or ext4 drives.

---

### Post by bodhi.zazen on 2010-08-08
> **lue42x said:**
> I have a new external harddrive (usb 2.0, 500gb) and I would like to use it with my Ubuntu laptop.  I don't intend on using it with other OSes so compatibility isn't really an issue.  The external drive is currently FAT32. I've heard this file system isn't as good as NTFS or ext4 (ext4 is what Ubuntu 10.04 uses right?) so I want to change the file system to either NTFS or ext4.

Are there any important advantages/disadvantages I should think about before formatting the drive?

Every file system has advantages and disadvantages.

The primary advantage of FAT or NTFS, IMO, is cross platform compatibility.

The down side, if you are not running windows, and the file system runs into a problem, it can be difficult or impossible to fix from Linux.

you can look at a site like this :

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Or this

[http://www.linux.org/lessons/advanced/x1254.html](http://www.linux.org/lessons/advanced/x1254.html)

or similar pages.

IMO if you do not run windows, I would consider ext2 or ext4 or jfs.

---

### Post by ezsit on 2010-08-08
Personally, I'd stick with ext3 since it has journaling and I doubt you'd see any benefit with ext4. ext3 has been battle-tested longer than ext4 and offers greater compatibility with other Linux systems, just in case you need to access from an older system.

---

### Post by linux18 on 2010-08-08
> **ezsit said:**
> Personally, I'd stick with ext3 since it has journaling and I doubt you'd see any benefit with ext4. ext3 has been battle-tested longer than ext4 and offers greater compatibility with other Linux systems, just in case you need to access from an older system.
ext4 is fully backwards compatible with ext3 you can read/write to ext4 from linux's made before ext4

---

### Post by bodhi.zazen on 2010-08-08
> **ezsit said:**
> Personally, I'd stick with ext3 since it has journaling and I doubt you'd see any benefit with ext4. ext3 has been battle-tested longer than ext4 and offers greater compatibility with other Linux systems, just in case you need to access from an older system.

IMO ext4 is stable enough and it is faster then ext3 (you will notice a difference in performance on low end machines and netbooks).

Every major distro will handle ext4.

---

### Post by lue42x on 2010-08-08
The consensus seems to be that given my circumstances, ext4 is the one to go with.  

I recently switched to Ubuntu 10.04 from Windows Vista and the gnu/linux community has made the switch really easy.  I appreciate it a lot!

Adel

---

### Post by linux18 on 2010-08-08
we are always happy to help!

---

### Post by drs305 on 2010-08-08
A couple of other considerations...

One more advantage of ext3/4 is their ability to fully incorporate linux permissions, which cannot be done with fat32/ntfs.

Although I use ext4, one advantage of ext3 is that there are several programs which can be used from within Windows to read ext3 files (ext2fs, for instance). Most cannot *yet* deal fully with the ext4 format - some claim to be able to do so but only can display the files.

---

### Post by lue42x on 2010-08-08
this happened when i formatted as ext4 ... this isn't anything to worry about is it?  Can I delete that file?

[http://img217.imageshack.us/img217/2442/lotsfound.png](http://img217.imageshack.us/img217/2442/lotsfound.png)

Its an empty file that takes up no space.

Also I noticed that when the hdd was empty with the FAT32 system, it had 465 gb free space, with ext4 it has 435.  Thats normal right?

---

### Post by drs305 on 2010-08-08
The 'lost+found' folder is a linux folder that is created when fsck is run. It is used as a place to store stray 'bits' found during the fsck check so the user can review them before deleting them. You can safely delete the folder, but it will return the next time the fsck check is run.

The reduced storage capability is possibly due to the 5% space reserved for system use in linux. This percentage can be reduced or eliminated with the *tune2fs* command if you really need the space. You can Google for more information about tune2fs or type "man tune2fs" in a terminal and read about the "-m" switch.

---

### Post by linux18 on 2010-08-08
> **lue42x said:**
> this happened when i formatted as ext4 ... this isn't anything to worry about is it?  Can I delete that file?

[http://img217.imageshack.us/img217/2442/lotsfound.png](http://img217.imageshack.us/img217/2442/lotsfound.png)

Its an empty file that takes up no space.

Also I noticed that when the hdd was empty with the FAT32 system, it had 465 gb free space, with ext4 it has 435.  Thats normal right?
yes, its safe to delete the lost+found file and the size difference is perfectly normal.
+1 for dropbox and seamonkey!

---

### Post by lue42x on 2010-08-08
cool, I totally don't need all that space though so I'll leave things as they are.  

And yes, seamonkey and (especially) dropbox - they're awesome lol

You guys are probably sick of hearing me say thanks .. .but uh ... thanks =D

---

### Post by linux18 on 2010-08-08
I never get tired of hearing "thanks" but on a less egocentric note you shoiuld mark the thread as solved.

---

### Post by CharlesA on 2010-08-08
Please note that if you delete the lost+found directory (it's not hurting anything to have it), you'll get prompted for fsck to create it then fsck will spit back an message that the file system was modified.

---

### Post by lue42x on 2010-08-09
Cool, I put "[SOLVED]" in the topic title (thats all i have to do to mark a topic solved right?).  I'll leave the lost+found folder as is since its no big deal to have it there - thanks for the tip.

---

### Post by renkinjutsu on 2010-08-09
It depends what you need the drive for. Are you just using it to store files to free up some space? If so, just use ext4 as stated before.

However, if you are storing media files that have to be plugged in to other devices (like a ps3 for example), you should go with FAT, even with all it's limitations (I don't like it either) =[

---

### Post by chopinhauer on 2010-08-09
> **linux18 said:**
> 
ext4 is fully backwards compatible with ext3 you can read/write to ext4 from linux's made before ext4


Unless the ext4 file system uses *extents*, in which case you can not mount it as ext3.

---

