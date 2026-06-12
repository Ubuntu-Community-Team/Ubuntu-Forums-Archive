---
title: "cannot delete this never ending file"
date: 2009-12-06
forum: General Help
---

### Post by Guitar John on 2009-12-06
This is one that I haven't encountered before.  I have an old file that I am trying to delete.  I do not know how this happened, but inside of that file is an empty file with the same name.  Inside of that, same thing.  I right clicked on it and clicked on properties.  As of right now, there are over 250,000 and still climbing.  The file size is over 8 GB.

I tried to delete it as root, and it locked up my system.  Any ideas?

---

### Post by falconindy on 2009-12-06
Might want to mention the path and name of the file.

---

### Post by wojox on 2009-12-06
I find it hard to believe you have no idea how this happened. Sounds like it's stuck in a loop. Open a terminal and run:

```
top
```

See if you can kill whatever is running so you can delete it.

---

### Post by Guitar John on 2009-12-06
The file is called JS.2.  It was originally on my remote hard drive, and called JS.  When I attempted to sent it to the trash, it went and JS.2 appeared in it's place.  The one in the trash is doing the same thing.

---

### Post by audiomick on 2009-12-06
Do you know which process created the file in the first place. The advice form wojox sounds good. If "top" doesn't do it for you , the GUI solution is the process manager in system> administration. Look for the process that created the file, stop it, and then try and delete.

---

### Post by MooPi on 2009-12-06
Does this sound like a malicious virus for Linux. The Blob that ate my hard drive UUUGH.

---

### Post by Guitar John on 2009-12-07
> **wojox said:**
> I find it hard to believe you have no idea how this happened. Sounds like it's stuck in a loop. 

> **audiomick said:**
> Do you know which process created the file in the first place. The advice form wojox sounds good. If "top" doesn't do it for you , the GUI solution is the process manager in system> administration. Look for the process that created the file, stop it, and then try and delete.



The file was part of a Music folder.  I have everything backed up on a USB hard drive.  There was a folder of MP3 files that I wanted to delete.  When I attempted to delete the folder (Right-click > move to Trash), another appeared in it's place.  

Top process was Xorg.  

I wound up backing up everything to a different hard drive, and then wiping out and reformatting the USB drive.  It's all good now.

---

### Post by gabo.cr on 2009-12-07
I know I probably shouldn't, but I find this thread hilarious.

---

### Post by Guitar John on 2009-12-07
> **gabo.cr said:**
> I know I probably shouldn't, but I find this thread hilarious.

???

---

