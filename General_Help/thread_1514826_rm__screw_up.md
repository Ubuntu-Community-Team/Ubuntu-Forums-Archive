---
title: "rm  screw up"
date: 2010-06-21
forum: General Help
---

### Post by bingcrosby on 2010-06-21
Hey guys,

I have a dual boot with ubuntu 10.04 (ext4) and ubuntu 9.04 (ext3).

On 10.04 I accidentally deleted a whole bunch of files with the rm command.  I installed extundelete in 9.04 which can undelete from ext4 file systems.  However, I can't access my 10.04 home directory in 9.04, as  /media/disk/home/asdf is empty except for two files README.txt and Access-Your-Private-Data.desktop.  I didn't delete all of it for sure.

Does anyone know how to make my 10.04 home directory visible in 9.04 so I can undelete?

Cheers!

---

### Post by gzarkadas on 2010-06-21
[The docs]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") say that your encrypted private directory is in ~/.Private. Activate the view of hidden files (select item `Show Hidden files' from the menu `View' in a nautilus window) and then cd to your home directory.

NB: The link has also information on how to mount the encrypted filesystem in case of emergencies; like the one you are now in.

Now if it happened that you did rm-ed your entire enctrypted fs, then use your undelete on the (now empty) home folder.

---

### Post by bingcrosby on 2010-06-22
Thanks.

I have managed to view my encrypted home folder on a a live cd, and it is not all deleted.  However, my undelete tool extundelete, fails to see anything in that folder.  Anyone else got alternative ext4 undelete tools that might work?

---

### Post by gzarkadas on 2010-06-22
See the tools mentioned [in this post]("http://ubuntuforums.org/showpost.php?p=9288271&postcount=4").

---

