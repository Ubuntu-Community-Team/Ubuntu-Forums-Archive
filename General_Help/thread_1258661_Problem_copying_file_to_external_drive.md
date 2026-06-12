---
title: "Problem copying file to external drive"
date: 2009-09-05
forum: General Help
---

### Post by rmcellig on 2009-09-05
I am trying to copy a file that is 7.8GB to my external USB drive. I took a couple of screenshots that may give you more info. The file I am trying to copy so that I can back it up is a Virtualbox guest OS file that is visible. Is there a better way for me to back up this file? Is it because of my external USB drive?

What are my options?

I have about 156GB of free space on the external drive.

---

### Post by NoaHall on 2009-09-05
Can you click on the details bit on the warning and post a printscreen of that for me? Thanks.

---

### Post by rmcellig on 2009-09-05
Here you go. See attached.

---

### Post by NoaHall on 2009-09-05
Then, at a guess I would say - 
You need to reformat your drive, because FAT can't support such large files

Or, if you're trying to copy a virtual hard drive, although it is really only 7.8GB, it's in theory much bigger - depending on how big you made it to begin with. Again, I think this would be solved by reformatting the drive.

If you need it with windows, use nfts, if you don't, use either ext4 or ext3

---

### Post by rmcellig on 2009-09-05
I had a suspicion it was the FAT format but I wasn't sure. Thanks for the info!!

Is it possible to copy it to one of my Mac formatted drives, I have hanging off of my iMac?

---

### Post by NoaHall on 2009-09-05
It depends on what format. The old HFS won't be able to support the size. The new ones will.

---

### Post by P4man on 2009-09-05
if its just a one time thing, you could split it in chuncks of 4GB or less (I think thats the FAT32 limit).

rar a -v3990M foo.rar foo

should make just under 4GB rars

---

### Post by rmcellig on 2009-09-05
great idea! Is there a RAR application I can install that will do this?


What do I do with rar a -v3990M foo.rar foo

Sorry, I'm pretty new to all of this

---

### Post by P4man on 2009-09-05
rar comes preinstalled. The command I gave should work, in a terminal
So just open a terminal (apps > accessoires > terminal)

then cd (change directory) in to the folder where that image is. 

```
cd .VirtualBox/HardDisks/
```

(or wherever you put it)

Then type something like:

```
rar a -v3990M /media/RSPORTABLE/somedir/backup.rar XP\ Pro.vdi
```

change the folder and file names accordingly. You dont have to type everything btw, you can press tab key to autocomplete file or folder names.

Keep in mind everything is case sensitive.

---

### Post by rmcellig on 2009-09-05
Thanks. I will try that out. I was just looking for a RAR utility with a GUI front end for Ubuntu.

---

### Post by P4man on 2009-09-05
actually.. I thought the GUI wouldnt have that option, but it does :)

Right click the vdi file, create archive, select rar as type (if you dont have it, install it > "sudo apt-get install rar") then click "other options", split in volumes of.. 3990 MB.

:)

---

### Post by rmcellig on 2009-09-05
I love it. Can't do this in OS X this easily plus you have password protection as well. This is fantastic! I love this kind of simplicity and I am sure with future releases of Ubuntu, it will only get better.

---

