---
title: "Thumbs.db:encryptable: what the heck is it and how do I get rid of it?"
date: 2010-04-28
forum: General Help
---

### Post by Warthaug on 2010-04-28
I am having a problem with grsync.  In some of the folders I am trying to backup there is a file named "Thumbs.db:encryptable"; yes, there is a colon in the name.

grsync always fails on this file; it throws an error saying it cannot access the file.  I can go into the folder containing this file, and remove it manually, after which grsync functions properly, and without error.

However, on occasion the file comes back, leading to a repeat of the problem.  

What is Thumbs.db:encryptable, where is it coming from, and how the heck do I get rid of it permanently?

Bryan

---

### Post by TitanusEramius on 2010-04-28
Thumbs.db is a Windows database-file for thumbnails in the current folder. I have not heard of a file called Thumbs.db:encryptable before, but chances are it's the same as the "normal" Thumbs.db.

In Windows it's possible to deactivate this function entirely, but Windows Explore will be somewhat slower to show the thumbnails because it's have to built them each time you open the folder. You might have to delete the Thumbs-files manually if you use this option, but ones deactivated in Windows and deleted you will not see them again.

Another solution would be to exclude this filetype from the backup, but I can't help you with this since i don't use grsync.

Hopes it's helps

---

### Post by Warthaug on 2010-04-28
Thanx, but I don't have windows installed on this computer; nor do I access this computer with a windows computer, so I don't think windows is the source of this file.

Bryan

---

### Post by ducktail on 2010-05-13
In my case, I have viewed some picture stored in an NTFS partition from Ubuntu. When I'm back to Windows, every folder I viewed has a Thumbs.db:encryptable file that I can neither delete or rename, which generates a whole lot of pain...

I was with 9.04 when this happened.

---

### Post by dudesurge on 2011-01-04
i have a similar/same problem
i've been using virtualbox for my windows needs, i've been using it for a while now and haven't seen this file until just recently at first i thought it wasn't a problem and for the most part it isn't but i downloaded a skin for something and in the zip folder was a file called "thumbs.db:encryptable" and thats when they started popping up in every folder with pictures in it and the only time i run into a problem is when trying to move the whole folder it says "i'm afraid i cannot do that" and sucks me inside, but all joking aside i think once you get one of these files somehow they just keep sprouting up everywhere and the only way to get rid of them is to just delete them manually

---

