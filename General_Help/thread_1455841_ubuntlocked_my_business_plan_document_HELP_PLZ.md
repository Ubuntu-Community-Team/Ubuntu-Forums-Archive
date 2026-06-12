---
title: "ubuntlocked my business plan document HELP PLZ"
date: 2010-04-16
forum: General Help
---

### Post by salem123 on 2010-04-16
hi all

i am not really ubuntu or computer literate got my business plan document locked without any action from me help plz

---

### Post by Sub101 on 2010-04-16
Locked in what way? 

What happens when you try to open it, and what format is the file?

---

### Post by salem123 on 2010-04-16
the format i believe is word document i choose 2007 (tried att local internet wont open too).and it was stored on my usb.thanx for assistance,mate

---

### Post by salem123 on 2010-04-16
oh yes
it has a little pad on the top right and wen i click open it asks copy for read and edit,or read only,and wen i try any of the two says error and gives me a blank document

---

### Post by Sub101 on 2010-04-16
OK. Can you either:

Using the terminal move to the folder and run 
```
ls -a FILENAME
```
This will display the file permissions

alternatively can you write click on the file, select properties and the permissions tab, and tell us who the owner etc is.

---

### Post by salem123 on 2010-04-16
thanks again

and owner says me but only read

---

### Post by kaldor on 2010-04-16
seems like just a permission change needed. I forget the command, it's chmod something. depends on the user.

---

### Post by salem123 on 2010-04-16
when i try permission change its states this, The permissions could not be changed.

---

### Post by salem123 on 2010-04-16
hallo guys
is anyone there
please please help....this should tell u how much am freaking out and i have been to iraq and afghan as a frontline infantry soldier, shot and wounded,now trying to get me life back with the business and plan lost.
please help.thanx.

---

### Post by eriktheblu on 2010-04-16
Please try
```
chmod +rw /path/to/file
```
If that doesn't work,
```
sudo chmod +rw /path/to/file
```

Please post the output if this doesn't work.

---

### Post by Jive Turkey on 2010-04-16
Its on a USB key that is probably formatted fat32 so the file permissions are probably not the issue.  I assume you are using openoffice in ubuntu no?  If so then open the file and look for the button in the toolbar between the email button and the export as pdf button.  I toggles edit mode for the currently open document.

Is there some reason you are using Word 2007 format?  Its not a terrible option if you are actually using Word 2007, but I have found the odf format to work fine in both ooffice and word 2010 beta.  Support for docx in ooffice is a little flakey as you have seen.  If the button doesn't enable editing try saving it as .odf and using that.

---

### Post by kanikilu on 2010-04-16
If this is on a USB flash drive, it's likely formatted as FAT32 or NTFS, so Unix permissions changes with chmod won't work...

Can you clarify if the file is still on the USB drive or if it's on your local hard drive?

//edit: jive beat me to it, see above.

---

