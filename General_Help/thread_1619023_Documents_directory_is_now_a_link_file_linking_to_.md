---
title: "Documents directory is now a link file linking to /home/user/Document and unaccessibl"
date: 2010-11-11
forum: General Help
---

### Post by didospear on 2010-11-11
Hi

I just realized that the "Documents" folder in my home directory has changed to a file which is a link to the /home/user/Documents and it is unaccessible. 

It does not (no longer) show in the "file browser"
when I try to click it from "places" it says:
Error:
Could not open location 'file:///home/user/Documents'
No application is registered as handling this file

When I list from the terminal (i.e. %ls -ltr )
it list the file (which was suppose to be the directory) as

lrwxrwxrwx    1   user   user   24  2010-11-01   18:20   Documents  ->  /home/user/Documents

NB. user in this case is my user name on the system, I am just using user for this forum.

I will appreciate your help on how to retrieve the information from the folder and remove the linked file to remain with the original folder

Dido.

---

### Post by The Cog on 2010-11-11
Ew! That's not nice.

Removing the link is easy - just delete the link as you would delete any other file. Command line "rm Documents" should do it.

Retrieving the original directory is less easy. If you can remember the name of one of the files in the original directory, you could do:
> sudo updatedb
locate *<filename>*
and see if it shows up.

---

### Post by didospear on 2010-11-16
> **The Cog said:**
> Ew! That's not nice.

Removing the link is easy - just delete the link as you would delete any other file. Command line "rm Documents" should do it.

Retrieving the original directory is less easy. If you can remember the name of one of the files in the original directory, you could do:

and see if it shows up.
Hi

Thanx for the reply. I am a bit afraid to remove the linked file "Documents" before I know if I can retrieve the files. However I tried what you suggested before deleting the file. The files do not show up. Does it mean that they can show up after I deleted the "Documents" file?

thanking you for your help in advance.

---

### Post by efflandt on 2010-11-16
What were you doing on Nov 1 that created that circular **Documents** symlink to itself.  That effectively wiped out the contents of that directory.  And because that was some time ago and updatedb runs daily, the files are no longer listed in the **locate** database.

I have been using Linux for 15 years, so I am very careful about deleting or overwriting files or directories from the terminal or using wildcards and am not familiar with tools for that.  But web search "linux file recovery".

---

### Post by theozzlives on 2010-11-16
If you've been actively using your computer that long, most likely your files are gone. That's why I preach "backup often" to my customers.

---

### Post by didospear on 2010-11-16
> **theozzlives said:**
> If you've been actively using your computer that long, most likely your files are gone. That's why I preach "backup often" to my customers.
Thanks people. LoL! I wish I knew what happened. I have no idea how the directory got deleted and the link file created. I personally do not like using link files. I never used it to be exact... But obviously I did something (most probably a mistype on the keyboard of something) that did this and I never realized it until it was late. I do not use the laptop that often though... but for sure I used it after that date. I will try recovery tasks like using "testdisk" and see what I can come up with.

---

