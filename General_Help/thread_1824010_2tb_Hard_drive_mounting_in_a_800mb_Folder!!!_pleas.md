---
title: "2tb Hard drive mounting in a 800mb Folder!!! please HELP!!!"
date: 2011-08-13
forum: General Help
---

### Post by Levitys on 2011-08-13
Ok guys i am having some serious trouble here. i recently installed ubuntu natty to replace freenas. i did this for the obvious reasons. i had a 2tb hard disk when i was runmimg freenas and it worked great. i went out and bought a 1tb so that i could have Ubuntu on it and then have the 2tb for my media. so here is the issue:

i installed natty on the 1tb flawlessly. put the 2tb in formated it to fat32 with the gpartition tool and setup up samba so i could read/write files with my laptop. perfect right? WRONG!!!!

The 2tb hd showed up on windows.......logged in......started to transfer my files......at around 800mb it said the drive was full......what? that cant be right......went back to Ubuntu clicked on properties.......1.8 tb.....thats right.....what the heck......then i noticed that the drive was mounted into a folder called media......can u guess the size of the folder? u got it...... around 800mb.

im at around 4 hours guys and i am ready to throw this thing out of my three story window.
whats going on here?

th 2tb is a hitachi from newegg
both hdd are internal

ANY help would be appreciated. 

thanks for ur time guys,
levitys

---

### Post by lmarmisa on 2011-08-13
Do not use FAT32. Define a partition of type NTFS for your 2 TB hard drive. FAT32 is too old and it has many limitations. NTFS works fine both in Ubuntu and in Windows.

---

### Post by Levitys on 2011-08-13
ok i formated the hdd to ntfs but still same thing....i havnt tried to transfer files yet but its still in this media folder.
here is a screen to explain what i mean......what would posses it to do this i dont understand.....it just seems to simple to mess up lol[IMG]http://www.foto.pk/images/screenihi.png[/IMG]

---

### Post by lmarmisa on 2011-08-13
Where is the problem?. The window located at left shows the free space of the media directory (/media). The free space of 858.5 GB belongs to the 1 TB hard drive.

If you have some doubts, open a terminal and type this command (be sure that the 2TB NTFS partition is mounted):

```

df -h

```

---

### Post by -kg- on 2011-08-13
> **Levitys said:**
> put the 2tb in formated it to fat32 with the gpartition tool and setup up samba so i could read/write files with my laptop. perfect right? WRONG!!!!

That ***might possibly*** be the problem.  Format the 2TB drive from the ***Windows side.***  Ubuntu is (generally) free and easy wheeling with partition formats, but Windows can be a bit persnickety with partitions not formatted to it's exact format (though it should be backward compatible with FAT32, but it's a possibility).  If you format the drive from the Windows side, it's at least formatted to what Windows wants.  Ubuntu should be able to read whatever's there.

Yet another reason so many of us have made "the big switch" and left Windows completely behind.  Hopefully that will work for you, though.

---

### Post by Levitys on 2011-08-13
It worked!

Last night i formatted the hdd to ntfs but i was so tired and frustrated i didnt check if the transfer worked. i just did and it worked!

thanks guys.....u Rock!

---

