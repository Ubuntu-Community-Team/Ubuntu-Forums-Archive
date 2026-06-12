---
title: "Openoffice.org document vanished?"
date: 2011-05-13
forum: General Help
---

### Post by sourcherry on 2011-05-13
Hi I'm new on here, and very new to Ubuntu altogether, so please ignore anything stupid I say haha
My father saved a document in openoffice.org on our Ubuntu computer, but it seems to have vanished. There is no icon in Documents (where he said he saved it) other than a zip file which doesn't have it in it. The only place I can seem to try to open it from is in OpenOffice itself under "Recent Documents", but when i click on it, it says "filename.odt does not exist", and i cannot right-click to open it with another word processor. I don't have backups enabled I noticed in OpenOffice's settings, but surely the document is somewhere! I checked in the trash but it's not in there. It's very important and he spent hours and hours on it, it would be terrible to try to write it again. I am very unfamiliar with the Ubuntu operating system as I myself have Windows 7, so please make any instructions simple, sorry!

---

### Post by SteveDee on 2011-05-13
> **sourcherry said:**
> ... but surely the document is somewhere!...

There is probably a search tool installed (check in the Accessories menu). Use this to look for recent files with the relevant extention (e.g. *.odt).

If you don't have a search tool installed, go to Synaptic and search for and install: gnome-search-tool.

---

### Post by jerrrys on 2011-05-13
open a terminal and enter

locate lostfilename

lostfilename being the name of the one your looking for

terminal is located in Asscessories

---

### Post by sourcherry on 2011-05-13
I tried searching for it but nothing comes up
My brother said that it looks like he saved it as a temporary, but doesn't know whether or not you can get them back. Can you?

---

### Post by wilee-nilee on 2011-05-13
Go to home, hit crtl-h shows hidden files go to the OO file.
.openoffice.org/3/user/backup 

If the backup is on it may be there.

---

### Post by sourcherry on 2011-05-13
> **wilee-nilee said:**
> Go to home, hit crtl-h shows hidden files go to the OO file.
.openoffice.org/3/user/backup 

If the backup is on it may be there.
the folder was empty :(

---

### Post by mcduck on 2011-05-13
since you mentioned a zip file in the documents directory, does the file happen to have the same name as the .odt file would have had?

Just came to mind because .odt files *are* zip files, with a bunch of xml documents zipped together. So if the zip seems in any way related to the missing document, you could try just renaming it into .odt.

(I don't know any reason why OO would end saving the file with wrong extension, though.)

---

### Post by grahammechanical on 2011-05-13
The Recent Documents list does not get updated if a document is moved or delete although it does give the location it thinks the document is in.

Does you father's computer have a Windows operating system installed on it? Windows has a My Documents folder. Does it not? Could he have saved it there? This is just an idea. You should see the Windows partition when you open the Places (File Manager) window. Click on it to mount it and OpenOffice will retrieve any documents that it records as being on that partition.

Regards.

---

### Post by col48 on 2011-05-13
locations for temporary files...
for instance
/{user's home folder}/.openoffice.org/3/user/temp
-- as its name starts with a . the openoffice.org is a hidden folder
/tmp
-- this is owned by root but you should be able to see the file/folder names in it.

You could also look in the trashcan.

It could also have been 'Export'ed rather than 'Save'd from OpenOffice, in which case it could have ended up as a PDF or XML or....

---

### Post by Hagar Delest on 2011-05-13
In the recent documents list, you should see what is the path of the file. Is it the temporary folder of your mail client or web browser? If so, the file has been deleted.

---

### Post by sourcherry on 2011-05-13
> **col48 said:**
> locations for temporary files...
for instance
/{user's home folder}/.openoffice.org/3/user/temp
-- as its name starts with a . the openoffice.org is a hidden folder
/tmp
-- this is owned by root but you should be able to see the file/folder names in it.

You could also look in the trashcan.

It could also have been 'Export'ed rather than 'Save'd from OpenOffice, in which case it could have ended up as a PDF or XML or....
the temp folder is also empty unfortunately :\
what does it mean if it has been exported? is there a way to get it?

---

