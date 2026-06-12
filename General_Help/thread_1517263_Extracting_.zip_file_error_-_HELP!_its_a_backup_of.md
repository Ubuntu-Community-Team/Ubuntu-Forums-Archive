---
title: "Extracting .zip file error - HELP! its a backup of my old computer!!!!!!!!!!"
date: 2010-06-24
forum: General Help
---

### Post by guyshoxton on 2010-06-24
[CENTER][SIZE="4"][FONT="Arial"]May some one please help me as fast as possible!? On my old ubuntu before i re installed it, i made a backup of all my files and my images and videos and compressed it and put it on my pendrive, but now after i tried extracting it on my re installed ubuntu machine (i use lucid - AKA ubuntu 10.04 LTS) it just gives me this error thing... [IMG]http://ipic.tk/s/mjm.png[/IMG] and i have a bunch of important files and images that are only in that zipped folder and i have no where else! and i am a web designer, my website files and images are all in that folder! its a total of 2GB the size of the folder, but it wasn't a problem compressing it, why is it extracting? because it was compressed as .zip on ubuntu 10.04 and i re installed ubuntu 10.04 and for some reason that pop up appears!!

PLEASE MAY SOME ONE HELP!!!!????:confused::confused::frown::frown:](*,)](*,)](*,)[/FONT][/SIZE][/CENTER]

P.S. this is what the error thing says: 


Archive:  /media/PENDRIVE/Documents.zip
Zip file size: 2147483647 bytes, number of entries: 36023

warning [/media/PENDRIVE/Documents.zip]:  end-of-central-directory record claims this
  is disk 32050 but that the central directory starts on disk 38692; this is a
  contradiction.  Attempting to process anyway.
error [/media/PENDRIVE/Documents.zip]:  missing 750403024 bytes in zipfile
  (attempting to process anyway)
error [/media/PENDRIVE/Documents.zip]:  start of central directory not found;
  zipfile corrupt.
  (please check that you have transferred or created the zipfile in the
  appropriate BINARY mode and that you have compiled UnZip properly)

---

### Post by oldos2er on 2010-06-24
You could try **zip -FF Documents.zip** from within the PENDRIVE directory. No guarantees it'll work tho'.

---

### Post by slooksterpsv on 2010-06-24
WINE + WinRAR works, in WinRAR on WINE, be sure to tell it to keep broken files, that way if the files are fine you can salvage still.

---

### Post by VH-BIL on 2010-06-24
> You could try zip -FF Documents.zip from within the PENDRIVE directory. No guarantees it'll work tho'.
This will try and fix the zip archive.

---

