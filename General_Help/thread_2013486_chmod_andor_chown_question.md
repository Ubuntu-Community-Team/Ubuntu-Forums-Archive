---
title: "chmod and/or chown question"
date: 2012-06-30
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-06-30
I'm archiving some files to clean up my desktop's harddrive and to make sure I don't loose data that I might need sometime in the future.

I did the following to the archive folder located on my desktop, assuming it would make all the folders and all the subfolders readable, writable and accessible to anyone at any time.


Code: 	sudo chmod -R 777 /home/artie/archive user   


"archive" is a large folder with many other files and folders in it, eventually I want to move it to a large USB drive for safe keeping.

I found out I couldn't rename the files in archive after the chmod command. I had to drop and drag the files to my desktop, make the filename change and drag and drop it back into the 'archive' folder.  BUT the system won't let me move the file from the desktop to the 'archive' folder.

After I juggle the files and folders around, I find some of them are owned by 'root' and some are owned by 'artie' (which is me). 

What do I have to do to the archive folder to make it readable, writable, movable and totally accessible to anyone at anytime on any system??

I already have files and folders on the USB external harddrive,  should I apply any changes to the entire USB drive as well?

Do I also have to do a chown command to the archive folder also? If so, who do I change the ownership to? 

I'm running Ubuntu 11.10.

TIA

Art

---

### Post by spikoley on 2012-07-01
Hopefully this will address your issue.

If they are your files they should be in your name and group.  I would also do the same with the folder they are in.

```
sudo chown -R <user name> /home/username/path/to/folder/
```
```
sudo chgrp -R <user name> /home/username/path/to/folder/
```

---

### Post by goodbye-windows(tm) on 2012-07-01
> **spikoley said:**
> 
If they are your files they should be in your name and group.  I would also do the same with the folder they are in.




OK, I had never thought of using the 'group' function.  Should the entire USB drive be changed as well??? I want to make sure anyone can access it at a later date, regardless of their username or the type of computer or their type of account they have.

TY.

Art

---

### Post by rai4shu2 on 2012-07-01
Since you haven't mentioned it, you probably should report the format of the drive you are working on. Is it FAT32, EXT, or some other file system? Not every file system properly supports permissions.

---

### Post by goodbye-windows(tm) on 2012-07-01
Hi rai4shu2,

Yes, you're right, I should have given that info.

All the partitions are ext4, done intentionally to keep Windows users out. This is the only exception to my read/write anytime/anywhere by any operating system policy.

I've thought about reformatting them to ntfs, as there might be a need my wife to use them (she has Windos XP required by her workplace) for her to access the files...but she has the use of 2 other ubuntu systems whenever she needs them, so we decided on ext4.

Regards,

Art

---

### Post by rai4shu2 on 2012-07-01
If you have need to access EXT in Windows, you can install this:

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by Vaphell on 2012-07-01
chmod -R 777 is not the best idea, because it also makes all files executable. Not the end of the world, i know, but it's good to be precise.

```
find <dir> -type d -exec chmod 777 "{}" \;
find <dir> -type f -exec chmod 666 "{}" \;
```

---

### Post by Morbius1 on 2012-07-01
Or even this would be better than a chmod -R 777:
```
chmod -R a+rwX /path
```The big "X" will make all directories executable but will only make executable those files that were executable to begin with.

---

### Post by goodbye-windows(tm) on 2012-07-01
Tnx Morbius1,

I used the following on my desktop folder that will soon be copied to the USB drive. 

```

sudo chown -R artie:artie ~/Desktop/archived 
chmod -R a+rwX ~/Desktop/archived 


```Tnx to all, I'll mark the thread as solved.

Regards,

Art

---

