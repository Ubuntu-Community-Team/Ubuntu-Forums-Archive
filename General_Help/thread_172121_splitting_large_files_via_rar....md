---
title: "splitting large files via rar..."
date: 2006-05-08
forum: General Help
---

### Post by robfindlay on 2006-05-08
Heres the problem.  I need to move large ISO files (6 to 9) gig from my linux box to a USB portable that is FAT32.  Obviously it wont work because size limitations on FAT32 soooo I want to use RAR to split them into 1 gig size files. I have read the man page but the syntax is throwing me. 

Example: 

File filmage.iso  

rar a -v<10> meh.rar fimage.iso 

I just get a syntax error everytime, can someone perhaps post up some examples? 

Or would gzip be easier?  It's just got to be something that XP can read.

TIA


Rob

---

### Post by aysiu on 2006-05-08
If you have no other valuable data on your USB device, you may want to think about temporarily formatting it as Ext3 and then using [FS-Driver](http://www.fs-driver.org/) to read the Ext3 device from Windows XP.

After that, you can reformat the USB device to be FAT32 again.

By the way, is this XP a separate computer or a separate partition/drive on the same computer?

---

### Post by robfindlay on 2006-05-08
[QUOTE=aysiu]If you have no other valuable data on your USB device, you may want to think about temporarily formatting it as Ext3 and then using [FS-Driver](http://www.fs-driver.org/) to read the Ext3 device from Windows XP.

After that, you can reformat the USB device to be FAT32 again.

By the way, is this XP a separate computer or a separate partition/drive on the same computer?[/QUOTE]

It's a second computer, i know i can move it over the network but that would saturate an already saturated network. 

fs-driver at least in my expierence doesnt work to well, i was just hopping there was a simple solution.

---

### Post by aysiu on 2006-05-08
How about using something like KDar (a graphical backup tool)? [It allows for the splitting of files](http://kdar.sourceforge.net/kdar-1.0.0-snapshots/KDar-1.0.0-settings-create-isolate-small.png).

---

### Post by robfindlay on 2006-05-08
Isn't there just some easy way to do this with rar or gzip? 

Rob

---

### Post by aysiu on 2006-05-08
[QUOTE=robfindlay]Isn't there just some easy way to do this with rar or gzip? 

Rob[/QUOTE] Probably, but I don't use those programs. Do you have something against KDar? It's in the repositories.

---

### Post by robfindlay on 2006-05-08
[QUOTE=aysiu]Probably, but I don't use those programs. Do you have something against KDar? It's in the repositories.[/QUOTE]

Does it create back up volumes in a format that can be read by an NTFS file
system? 


Rob

---

### Post by aysiu on 2006-05-08
[QUOTE=robfindlay]Does it create back up volumes in a format that can be read by an NTFS file
system?[/QUOTE] Sure. Look at the screenshot I linked to before--you get compression options: None, gzip, bzip2. Use none and split the file after 4 GB.

---

### Post by robfindlay on 2006-05-08
[QUOTE=aysiu]Sure. Look at the screenshot I linked to before--you get compression options: None, gzip, bzip2. Use none and split the file after 4 GB.[/QUOTE]


Got it...TKNS, i was way bleary eyed last night when i looked at it.

---

### Post by rommel_rco on 2007-09-17
//rar a -v<10> meh.rar fimage.iso

to split the file

use this command

rar a -v10m meh fimage.iso

this split the file into 10 Megabytes with the filename meh and the file to be splitted is fimage.iso

---

