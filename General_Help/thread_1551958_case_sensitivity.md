---
title: "case sensitivity"
date: 2010-08-13
forum: General Help
---

### Post by worksofcraft on 2010-08-13
You know I am so totally annoyed by case sensitivity in file names and paths and things #-o

Is there anyway to turn it off so that dsc1024.jpg and DSC1024.JPG and even Dsc1024.jpg all just become one and the same identifier?

---

### Post by dino99 on 2010-08-13
select these files by right click and change their properties

---

### Post by Vaphell on 2010-08-13
well, in linux dsc1024.jpg and DSC1024.JPG and even Dsc1024.jpg can exist simultaneously, i don't see how it should be allowed to disable case-sensitiveness completely.

you can do what you need with a script, plenty of ways to achive desired effect here:
[http://www.linuxjournal.com/content/convert-filenames-lowercase](http://www.linuxjournal.com/content/convert-filenames-lowercase)
but be warned that you can/will overwrite a file if collision occurs

---

### Post by worksofcraft on 2010-08-13
> **Vaphell said:**
> well, in linux dsc1024.jpg and DSC1024.JPG and even Dsc1024.jpg can exist simultaneously, i don't see how it should be allowed to disable case-sensitiveness completely.

you can do what you need with a script, plenty of ways to achive desired effect here:
[http://www.linuxjournal.com/content/convert-filenames-lowercase](http://www.linuxjournal.com/content/convert-filenames-lowercase)
but be warned that you can/will overwrite a file if collision occurs

Well all those files were once from the same source and at one time someone used "CammelCase" to make names more legible.

You see in those days putting spaces in file names was not possible (and I think allowing them has created a lot more problems, but that is a different issue).

Then someone used clever scripts to convert all the names to upper case... and someone else used cool scripts to convert them all to lowercase... and they both made various backups...

While mixing upper and lower case characters in a file name can be useful saying that they are then different files just creates problems, specially since internet doesn't take upper/lower case into account. I just want to turn case sensitivity off... not convert all my file names to end up with even more duplicates :confused:

---

### Post by Vaphell on 2010-08-13
why would you end up with more files than you already have? renaming is renaming, number of files is constant. i can see a problem in case if you'd merge your collection with some other set of files which has case-sensitiveness problem again.
if you are sure all variations of the same file name have the same content, brute force renaming would in fact reduce the number of files because 3 different files would be renamed to the same destination name - 1 file from 3. Fancier script can have safeguards if needed

i think disabling is impossible because in case of 3 different names where case-sensitiveness is the only difference you wouldn't get an unique handle and there would be no way to unambiguously identify files.

---

### Post by worksofcraft on 2010-08-13
I have thousands of these old files and only get them onto my computer when I need them from their CD Rom backups.

If I convert all the files I have on my hard drive right now to lower-case, then any that didn't exist in a lower case name before now do and so are liable to become duplicates if I bring more in from the  CD Roms :(

However someone just told me that NTFS doesn't have case sensitivity so all I would have to do is use an NTFS partition when working with these files on my computer. I'm about to try this once I've formatted a suitable partition.

---

### Post by worksofcraft on 2010-08-13
- Update -

Looks like I was misinformed:
NTFS can store separate files with the same name that differ only in character case. I made one called ANewFile.txt and another called ANEWFILE.TXT and put something different in each.

Then I booted to Windows and tried to create a third one named anewfile.txt but it told me I already had a file of that name.

Under Windows the other two files were both still there and when I opened them they were still different. However on editing one of them both were modified to have the same data... could even have left some orphaned clusters on the disk.

I'm thinking my best bet is to do the work under Windows which will prevent me from ever creating duplicates in the first place.

---

### Post by sdennie on 2010-08-13
If the problem is that it's annoying to get the case right on the commandline, you could add the following to ~/.inputrc (create it if it doesn't exist):

```

set completion-ignore-case on

```

Close the terminal and open a new one.  Now tab completion is case insensitive.

---

