---
title: "how to replace fstab"
date: 2009-11-14
forum: General Help
---

### Post by jimric on 2009-11-14
I am using ubuntu 9.10 and I need to replace my fstab file how do I go about doing this in ubuntu 9.10 since some things have changed in this version.
Thanks in advance.
Jim

---

### Post by Zoot7 on 2009-11-14
Can you provide a bit more information as to why you've an issue with fstab?

---

### Post by ooze on 2009-12-22
Hi guys,
First of all - Im a total newbie to Linux. 
 
I edited the fstab file to add
 
usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 
 
to the partition with the mount point /
 
(reference link [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p4))
 
I made a mistake on the file and saved without realising it. I need to somehow re-edit the file to fix the typo. When I try and edit the file:
 
vi /etc/fstab
 
I can insert and edit but the message 
 
W10:Warning: Changing a readonly file
 
is displayed. Using w! also produces a message 'Can't open file for writing'.
 
If you could provide me with a possible solution it would be much appreciated.
 
Regards
oOZe

---

### Post by Elfy on 2009-12-22
Never used vi - bit I would guess you need to open with sudo to get root rights.

sudo vi /etc/fstab

---

### Post by ooze on 2009-12-22
Thank you for your response.
 
I am logged in as root. Still cant edit the file. Is there any other way that I can replace this file somehow?

---

### Post by vanadium on 2009-12-22
> First of all - Im a total newbie to Linux.

I edited the fstab file to add

First a general advise: it is wise to learn the system first, then proceed to more advanced system administration.

Look in the directory /etc. Chances are that the editor you used created a backup copy of your original file there. Then you can replace the current one by the backup.

---

### Post by ooze on 2009-12-22
vanadium
 
Certainly a wise comment about getting to know the basics first. Running before you can walk wasnt always an option :)
 
Im busy rebuilding the setup as we speak. Couldnt find the duplicate in the etc directory. 
 
Would you perhaps be able to recommend any suggested reading material for total newbies? As in - what document could let me move over from being a total MS nut to the Linux environment?
 
oOZe

---

### Post by muteXe on 2009-12-22
> **ooze said:**
> Thank you for your response.
 
I am logged in as root. Still cant edit the file. Is there any other way that I can replace this file somehow?

Hiya,
What do you mean "logged in as root"?

Ta,
mute

---

### Post by vanadium on 2009-12-22
Just buy a good book on "beginning ubuntu" or something in the local library. Even without that: there are introductory manuals on the Canonical website and accessible documentation.

---

