---
title: "Unison sync to fat32 permissions"
date: 2010-04-03
forum: General Help
---

### Post by gmport on 2010-04-03
My system consists of a laptop running Ubuntu 9.10, a network drive (Samba share formatted fat32 the only option) and a desktop PC running Windows XP.
 
For several weeks have been trying to set-up Unison to synchronise files between my laptop and a network drive with only limited success.
 
I mount the network drive locally with:
 sudo mount -t cifs //netdrive/store /home/gm/NAS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777.
 
Then in Unison (graphical interface),
 root 1 is: /home/gm/Shared_Docs
 root 2 is: /home/gm/NAS/HomeBackup/Shared_Docs_Backup
 After clicking the “OK” button, Unison searches for changes files and I click “Go”.
 
An error is then produced, a sample of which would be:
 “Error in renaming /home/gm/NAS/HomeBackup/Shared_Docs_Backup/.unison.Our-inv.xlsx.f3e8034159989f9de7081f9154319a2b.unison.tmp to /home/gm/NAS/HomeBackup/Shared_Docs_Backup/Our-inv.xlsx:
Input/output error [rename(/home/gm/NAS/HomeBackup/Shared_Docs_Backup/.unison.Our-inv.xlsx.f3e8034159989f9de7081f9154319a2b.unison.tmp)]”
 
If all files in the destination directory (root 2) are first deleted, all files are copied correctly without errors so, I think the problem may be caused by permissions where Unison is unable to overwrite the original file. I know formatting the network drive fat32 is probably making the matter worse, unfortunately I have no alternative.
 
I've also had a very similar problem using Grsync so if anyone tell me how to solve this problem, I would be most grateful.
 
Regards
 gmport

---

### Post by dcstar on 2010-04-03
> **gmport said:**
> My system consists of a laptop running Ubuntu 9.10, a network drive (Samba share formatted fat32 the only option) and a desktop PC running Windows XP.
 
For several weeks have been trying to set-up Unison to synchronise files between my laptop and a network drive with only limited success.
 
I mount the network drive locally with:
 sudo mount -t **cifs** //netdrive/store /home/gm/NAS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777.
........
I've also had a very similar problem using Grsync so if anyone tell me how to solve this problem, I would be most grateful.


Firstly, a CIFS mount is a NTFS mounf, not FAT.

Secondly, NTFS does not support names beginning with "."

---

### Post by gmport on 2010-04-04
Thank you for your reply David. As you've probably guessed, I'm still very much a beginner. Could you tell me how I should mount a fat network drive?

Regards
Geoff.

---

### Post by HermanAB on 2010-04-04
$ man mount

Read through the man page.  FAT doesn't support Unix-like permissions, so you cannot use rsync or unison to a FAT drive.

If you want to make proper backups then you got to use a proper file system on the other end, not a 40 year old kludge.

---

### Post by gmport on 2010-04-04
Thank you Herman, I thought I may be banging my head against a brick wall. 

Kind regards
Geoff

---

### Post by brm on 2010-05-06
> **HermanAB said:**
> FAT doesn't support Unix-like permissions, so you cannot use rsync or unison to a FAT drive.

If you want to make proper backups then you got to use a proper file system on the other end, not a 40 year old kludge.

@HermanAB,
I agree with your disdain towards FAT filesystems.

To go from there, however, to say that neither rsync nor unison support FAT is simply incorrect. As you suggested, read the man pages. The support is extensively documented.

I have been successfully using rsync to transfer between FAT and *nix filesystems for years; in fact, I rely on it to some extent. On the other hand, I have never succeeded in getting unison to work satisfactorily. I believe, however, that is my own failure and not a failure, either of the application, or even of the Microsoft filesystem which it supports.

---

### Post by joemun on 2010-06-30
If you add:
owner = false
perms = 0

at the beginning of the .prf file on the unison hidden folder (.unison) in your home directory, you may be able to sync to a FAT file system to and from a linux file system...

---

