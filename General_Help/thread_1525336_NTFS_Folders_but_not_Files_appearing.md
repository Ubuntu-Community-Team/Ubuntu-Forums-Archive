---
title: "NTFS Folders but not Files appearing"
date: 2010-07-06
forum: General Help
---

### Post by Glebbity on 2010-07-06
Hello everybody,


I recently had a Windows Vista laptop crash and burn because of some damage done to all the lovely files Windows cannot boot without. Since my computer cannot boot from USB normally I used PloP Bootmanager to get it to boot from a live Ubuntu image on a USB stick. 



 Before I install Ubuntu, I want to recover some of my files sitting on the disk, and the partitions seem to mount in the GUI- I can see them, I can click mount or unmount and it responds. The trouble is that while I can see all of the folders on the Windows partition: Program Files, Documents and Settings, etc. I can't see any of the actual files. The disk itself is reported to have data on it- even Ubuntu recognizes it's almost full, but every folder has 0 files with the exception of /media/[A particular character string] which has three boot-related files. This is true whether I use bash as root or not. I've tried mounting to a different point and remounting via the terminal using ntfs-3g and editing the fstab file to recognize the parition with full permissions, but nothing seems to work.
 I've tried to be as detailed as possible and any help is much appreciated.

---

### Post by Glebbity on 2010-07-08
Can anyone help me? I'm using someone else's computer these days, and they're going to need it back soon. I don't want to lose all my data.

---

### Post by jkid on 2010-07-08
bump......for help..!!

---

### Post by lmarmisa on 2010-07-08
Hi Glebbity,

I do not know PloP Bootmanager, but try to use any Ubuntu Live CD (for example, 9.10 or 10.04). Ubuntu is able to read NTFS files.

It sounds very strange that all the contents of the different files are been damaged but not the directories. I suppose that you will be able to recover your files.

Kind regards,

Luis

---

### Post by Glebbity on 2010-07-08
Well PloP is just a way for me to boot a live USB- so I can make changes and store information on the OS. It's probably not an important detail, but I included it just to be thorough. I don't know, I baffled- I can't fathom why my files aren't accessible but the directory tree is clear as day. Could it be because I had a password protected Windows account? I know the password, but it shouldn't matter since the whole Windows system went screwy after I installed a .net framework update. Key OS disk sectors went "bad" but I'm pretty sure that's not actual damage so much as OS stupidity. Ubuntu picks up on the bad disk sectors, but I'm not sure that should be too much of a problem since I can see the files. I'd expect maybe some bad or corrupted data- but no data at all? It just seems unlikely.

ETA: I can connect to the Internet through the problem box if anyone wants screenshots.

---

### Post by lmarmisa on 2010-07-08
Ubuntu is able to read NTFS files if the file system is not encrypted. You say that your Windows account is protected with a password. If so, Ubuntu should be able to read your files. The thing would be different if the NTFS partition would be encrypted with a password.

---

