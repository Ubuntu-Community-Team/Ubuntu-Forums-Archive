---
title: "OpenOffice locked file"
date: 2012-08-02
forum: General Help
---

### Post by Noo 2 Ubuntoo on 2012-08-02
Hi, Any one know how I can open an Open Office locked file?

I run Ubuntu 10.04 with Gnome 2 desktop (standard Ubuntu installation). I have an Open office spreadsheet I saved in Excel format but can't open. When I try to open nothing happens but there is a file underneath titled ".~lock.performance.xls#". The actual name of the file I'm trying to open is "Performance.xls". A search of the "properties" of the file says it is locked for editing by me! I'm confused. 

The run up to this event was that I had been editing the file (which is on a flash drive) and left the computer unattended (at home on my own so no one else could have interfered with it) which then powered itself down after a few minutes. 

Upon rebooting and signing in, the icon for the flash drive had disappeared and a search of "Places" failed to show the flash drive too, although it was still plugged in and the "active" light (which is part of the flash drive) was still on. As I couldn't find the drive on the computer to safely unmount I pulled the drive out. When I put the drive back in again I couldn't access the file.  

I guess I shouldn't have pulled the drive out as it seems there is still an editing process running on it, but is there any way I can safely kill this editing process so I can open the file again?

---

### Post by LewisTM on 2012-08-02
The lock file is created when you edit a file and erased when you close it. If a power failure interrupts the process, you end up with an "orphan" lock file. For some office software, this says the file is still locked for editing, even though it's not open. For others, it says the file should be recovered. Delete the lock file and try again.

Cheers!

---

### Post by Noo 2 Ubuntoo on 2012-08-02
Thanks Lewis TM. I tried that but now I get a dialogue box saying "Performance.xls is locked for editing by unknown user" it goes on tell me to open the document as read only or to open a copy of the document for editing. No matter which option I choose a blank "writer" ( as in the Open Office Word Processor) file is displayed.

Any ideas?

---

### Post by LewisTM on 2012-08-02
Mmm not many ideas. You could try renaming the file and see if that helps. 

The fact that opening a copy give you a blank document is bad news, smells of an old bug in OOo that would zero-byte files upon disk failure. What's the size of your file?

---

### Post by Noo 2 Ubuntoo on 2012-08-02
Renaming the file has changed the behaviour. 

I now get a Text import dialogue box asking what language and character set etc I want to use. Upon confirming the English version, I get the "Document in Use" dialogue box inviting me to open the file as read only or a copy.

When I choose "read only" I get a  "Read error" message saying the data couldn't be read. However, if I choose "open copy" I am now presented with a blank Calc spreadsheet (as opposed to the blank writer file previously).

File size = 74.5 KB

---

### Post by LewisTM on 2012-08-02
The good news is that your file is not zero byte. The bad news is that your USB file system is probably corrupted (read errors, incessant denied access). You should run a disk check/repair utility on it. You chances of getting a readable file are slim to be honest.

---

### Post by dreamquartz on 2012-08-02
If you save it as an odf-file again you can edit it normally.

Dream

---

### Post by Noo 2 Ubuntoo on 2012-08-02
Thanks for suggestions - the odf rename made no difference but regarding the USB file system. Are you saying the **entire** file system on the drive is corrupted? 

I can open any other file on the flash drive - it's only this one that's giving problems.

---

### Post by LewisTM on 2012-08-02
That's good, then it's probably just the file entry that's wrong.
You should still run a check, that will give you a clue. I suggest you backup important files before attempting any repair.

---

### Post by audiomick on 2012-08-02
[QUOTE=Noo 2 Ubuntoo;121Are you saying the **entire** file system on the drive is corrupted? [/QUOTE]

I wouldn't like to say it is, but I reckon it is possible after the sequence of sleep-power down-drive removal events that you described. It seems to me at least to be certain that Open Office didn't get to cleanly finish it's business.

---

### Post by Noo 2 Ubuntoo on 2012-08-02
Ok thanks for the help guys. I think it's just the one file that Open Office didn't complete properly on thats problematic, as I've now tried opening scores of other files in other formats too and they are all OK. It's 11:30 pm here so I'm signing off now and I'll try the disk repair tomorrow, after I've backed everything up. I understand these repair utilities are notorious for doing lots of further damage.

Once again thanks for the help.

---

### Post by dreamquartz on 2012-08-02
Sometimes when I download or try to use a MS file, it is locked. It shows a similar message as yours.

I do not know exactly when it happens, but when it does, the only way is to safe it as an ODF-file. Then the ODF-file can be opened. At that point it can be manipulated as how it should by LO/OOO.

Dream

---

### Post by ing.tani on 2012-08-03
Try to upload and open it online. [http://www.viewdocsonline.com/]("http://www.viewdocsonline.com/")

---

