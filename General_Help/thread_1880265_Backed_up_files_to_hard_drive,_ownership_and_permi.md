---
title: "Backed up files to hard drive, ownership and permission issues"
date: 2011-11-13
forum: General Help
---

### Post by u-noob-tu on 2011-11-13
Yesterday i backed my sister's computer, which was running Ubuntu 8.10, to an external hard drive so i could update the computer to Oneiric. Everything went fine until i put everything back on the computer with Oneiric. It seems that all the files and folders i put back are still owned by root from Ubuntu 8.10. i tried changing ownership using "chown" on the home folder, but i hit two issues every time i try. first, there is a folder that got copied over called ".gvfs" which cant be deleted. i get a message saying that resource or directory is busy. there is nothing in the folder, though. second, i can use "chown" on individual folders within the home folder, e.g. /home/Music. however, this seems to only change the ownership of that folder, and nothing actually in the folder, e.g. /home/Music/everything/below/Music. ive been able to change the permissions of subfolders as root, but only one folder at a time, and my sister has 23gb of stuff. is there a faster to do this?

---

### Post by Wayne_V on 2011-11-13
chown -R ...  (see 'man chown')

---

### Post by herta on 2011-11-13
You can ignore the .gvfs.  GVFS stands for Gnome Virtual FileSystem, and is used by samba, sftp, webdav and such.

---

### Post by u-noob-tu on 2011-11-13
whenever I try to do "sudo chown -R $USERNAME: /home/username" it won't work because something is using .gvfs. the folder is empty, though. how can I fix this while at the same time applying the same permissions to every sub- folder and file?

---

### Post by Wayne_V on 2011-11-13
try "umount .gvfs" first

gvfs filesystems are accessible only by the owner.  not root.

---

### Post by u-noob-tu on 2011-11-13
> **Wayne_V said:**
> try "umount .gvfs" first

gvfs filesystems are accessible only by the owner.  not root.

do you mean do "umount .gvfs" as root? like "sudo umount .gvfs"?

---

### Post by u-noob-tu on 2011-11-13
okay, i managed to delete .gvfs by using umount. however my second problem still exists, in that i can change the permissions of a directory, but it wont affect any directories beneath it.

---

### Post by Wayne_V on 2011-11-13
you are using "sudo chown -R user /path" ?   Is /path a symbolic link?  If so you need the -H or -L option.  You could try adding -v as well.

---

### Post by u-noob-tu on 2011-11-14
> **Wayne_V said:**
> you are using "sudo chown -R user /path" ?   Is /path a symbolic link?  If so you need the -H or -L option.  You could try adding -v as well.

I finally got ownership taken care of by using "sudo chown -HLRv $USERNAME: /home/user" thanks for the tip.

---

### Post by Roasted on 2011-11-14
**chown fred home**   -  just makes fred the owner of "home"
**chown -R fred home**   -  makes fred the owner of "home" AND everything beneath it.

You ran: chown -HLRv

-HLRv is the same as
-H -L -R -v

So in essence, you ran the -R, just with extra switches involved as well. :guitar:

---

