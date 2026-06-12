---
title: "Cant move files saved from Ubuntu to Windows"
date: 2012-10-04
forum: General Help
---

### Post by Mazate on 2012-10-04
Howdy

I moved a bunch of files (Pictures, music, etc) over to an external hard drive from my Ubuntu installation.  I'm now trying to move those files from my external drive to a windows 7 computer but I'm unable to move them.  It's as though windows will not accept the files and it won't let me drag them over.  Any help would be most appreciated.

---

### Post by tienlbhoc on 2012-10-04
you can use ext2explore (support ext4 format)

---

### Post by Mazate on 2012-10-04
> **tienlbhoc said:**
> you can use ext2explore (support ext4 format)

Will that then enable windows to read the files and use them?

---

### Post by ajgreeny on 2012-10-04
How is the external disk formatted, and can you even see the files you want to drag over when you look for them in windows or have you no access at all to them?

---

### Post by Mazate on 2012-10-04
> **ajgreeny said:**
> How is the external disk formatted, and can you even see the files you want to drag over when you look for them in windows or have you no access at all to them?

To the best of my knowledge its formatted in NTSF because there are other files on that same drive that I'm able to move between the drive and windows without any issues, mainly because they were originally moved there from a windows computer.  As far as the Ubuntu files go (this is actually a copy of my Ubuntu One backup stuff) I can go through them and see them all without any problem on the windows computer.  It just won't let me move them to the windows computer.

---

### Post by Wim Sturkenboom on 2012-10-04
Which intelligent error message is Windows giving you?

---

### Post by Mazate on 2012-10-04
> **Wim Sturkenboom said:**
> Which intelligent error message is Windows giving you?

No error at all.  I plug in the drive and then go into windows explorer.  I can see all the files on my external drive fine.  I go to grab the folder they're in and then drag them over to a folder on the C drive of the computer.  I drag it over but then nothing happens.  It doesn't give me an error or anything.  It just refuses to move the files over.  I have other files on the same external drive that were added by another windows computer.  Those I can move fine.  The ones that came from my Ubuntu laptop, however, just cannot be moved over.  I drag & nothing happens.

---

### Post by Wim Sturkenboom on 2012-10-05
Have you tried <ctrl>c to copy the source folder and next <ctrl>v to paste at the destination?

Can you open files (e.g. images, docs, ...) under Windows in the specific folder on the external HD?

---

### Post by Mazate on 2012-10-05
> **Wim Sturkenboom said:**
> Have you tried <ctrl>c to copy the source folder and next <ctrl>v to paste at the destination?

Can you open files (e.g. images, docs, ...) under Windows in the specific folder on the external HD?

I've tried copy/paste and it didn't work.

Yes, I can open files and view them fine.  In fact, I can drag individual files over file.  I just cant drag whole folders and since I have thousands of files, dragging over each one individually would be quite a job. :(

---

### Post by ajgreeny on 2012-10-06
This may be a bit of a longshot, but do you already have a folder by the same name as the one you are trying to drag across, even if it is named in a different case, eg **Folder** and **folder, **which are exactly the same in windows, but not in Linux.

---

