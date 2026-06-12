---
title: "gFTP Permissions"
date: 2006-06-21
forum: General Help
---

### Post by medw1974 on 2006-06-21
I am trying to do a backup of my website to my local machine but when I try to use gftp to do the transfer it says it doesnt have permission to write. 

I am trying to transfer to a folder under /home/michael/ on my login.

Any ideas?

---

### Post by medw1974 on 2006-06-21
Actually if I sudo gftp it looks like it is copying the files but only 0 bytes files are writtrn to the drive.

---

### Post by odysseus.lost on 2006-06-21
1. Do you really have write permissions to this directory?? You can check with ls -l
2. Do you still have free space on this partition of your hard disk?

---

### Post by medw1974 on 2006-06-21
1. drwxr-xr-x   7 michael michael     4096 2006-06-21 15:05 fb2b
2. yes

I shall try making the folder writable by all and see if that helps.

I also installed KFTPGrabber which seems to transfer ok but keeps crashing.

---

### Post by medw1974 on 2006-06-21
Changing the permissions to:

drwxrwxrwx   8 michael michael     4096 2006-06-21 15:24 fb2b

does not make a difference.

---

### Post by odysseus.lost on 2006-06-22
Just out of curiosity... can you ftp with another ftp client?? Even the file browsers can ftp and see what happens? You may also want to have a quick look on the preferences of your gftp File->Options and see fi there is anything strange there.... Also can you ftp to another site and check that gftp is working fine?

---

### Post by medw1974 on 2006-06-22
I tried KFTPGrabber which does transfer the files ok, but keeps crashing on me.

GFTP produces the same symptoms on other ftp sites as well.

I can't see anything obvious in the options, my guess is that it is some sort of permissions issue but can't figure it out at all.

---

### Post by medw1974 on 2006-06-22
I've ended up using the ftp client built into nautilus (didn't even know there was one) and this seems to be bringing me success.

---

### Post by odysseus.lost on 2006-06-22
I am glad it's working... If you really want to use gftp you can try unistalling it and installing it again... Bear in mind that synaptic uninstallation will not remove all the dependencies and you will have to do it manually yourself. Otherwise you can get the source code, compile it and install it yourself...

---

