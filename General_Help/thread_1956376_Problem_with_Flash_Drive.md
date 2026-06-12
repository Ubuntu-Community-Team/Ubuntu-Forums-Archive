---
title: "Problem with Flash Drive"
date: 2012-04-10
forum: General Help
---

### Post by craig10x on 2012-04-10
A friend of mine gave me a sandisk cruzer 8gb flash drive...i am using ubuntu 12.04....

There's no problem as far as the flash drive being recognized when i plug it in, and the video files he put on it for me all show up in the window...

I deleted most of those files, and decided to transfer in a few on my own...
so i copied and pasted them into the flash drive but was not successful...
a window comes up and shows an error and says something about exceeding the limit (in terms of space)...

This is actually not the case...i had only 2 gb worth of video files on it and was only transferring in 4 gb additional...but it will not transfer (insisting that it exceeds the limit)...

What could possibly be the problem?   And how would i rectify it (in a hopefully easy manner...lol) 

Thanks;)

---

### Post by abyrne on 2012-04-10
Is the flash drive partitioned in FAT32? If it is, the max size for an individual file is 4GB. So if it's one huge video file, that may be the source of your problem.

---

### Post by craig10x on 2012-04-10
I believe it is...but although i was trying to transfer several (actually 4) video files in at one time, each individual file was approx 1gb or less...
and i only had about 2 gb of files already on the drive...(and none of those files were larger then about 1gb either)...

By the way, i didn't do anything with it...my friend had added in some files before he gave it to me (he probably did it on windows)...and after copying some files out from it on to my own hard drive, i deleted most of them and then was trying to add in these new files i described...

---

### Post by scradock on 2012-04-11
> **craig10x said:**
> I believe it is...but although i was trying to transfer several (actually 4) video files in at one time, each individual file was approx 1gb or less...
and i only had about 2 gb of files already on the drive...(and none of those files were larger then about 1gb either)...

By the way, i didn't do anything with it...my friend had added in some files before he gave it to me (he probably did it on windows)...and after copying some files out from it on to my own hard drive, i deleted most of them and then was trying to add in these new files i described...

Probably the "delete" you did just marked the files as being in the "Trash" folder, so they're still there on the flash drive, taking up space. Open the drive in Nautilus, with Hidden Files showing, and check if there is a Trash folder in it. If there is you should be able to empty it - even delete it if necessary. That should really make the space available.

The Properties menu item (from right-click menu) should tell you how much free space you have. You might like to check that before and after doing what I suggested above.

Ahh! if it's a FAT32 format, the Trash folder might be called something like $RECYCLE.BIN, or some other informative name. Treat it the same...

---

### Post by craig10x on 2012-04-11
I checked in the "disk utility" and it looks like this flash drive was formated for windows...my friend runs windows and linux on his computer and the drive functions properly both when he is using windows xp and linux mint 10 which is also on his hard drive...

I only run Linux...have no windows partition (wiped it out when i installed ubuntu)
Does this flash drive need to be formatted differently?  if so, to what? and can that be done with "disk utility" ?

I checked "hidden folders" on the flash drive and it shows that there is a trash folder on this drive and that is where the files that i deleted has gone to...which i guess may explain why i can't add additional files and it's telling me i would exceed the limit...

It seems like i am unable to empty the trash though...i tried that but the files don't leave the trash folder...and if i try deleting them they pop right back in the trash folder...

Anyone have any ideas about this?  I never used a flash drive before on linux so i am rather clueless on this...

---

### Post by craig10x on 2012-04-11
With my friend's assistance we finally figured it out....in order to empty the flash drive's trash i had to highlight the files within it and then do:  shift/delete at the same time, and was given the option to permanently delete those files....

Once i did that, it freed up the space i needed and was able to transfer in my new files...

The problem was i was just hitting delete not shift/delete and that is why it was going to the flash drive's trash folder....

Now...all is well...thanks to those who tried to assist me ;)

---

