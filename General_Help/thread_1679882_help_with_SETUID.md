---
title: "help with SETUID"
date: 2011-02-01
forum: General Help
---

### Post by Robx610 on 2011-02-01
anne-hicks@uhome:/tmp$ ls
leptonlib-1.67  tesseract-3.00  TEST
anne-hicks@uhome:/tmp$ chown -R anne-hicks TEST
anne-hicks@uhome:/tmp$ chmod -R 6770 TEST
anne-hicks@uhome:/tmp$ cd TEST
anne-hicks@uhome:/tmp/TEST$ umask 0007
anne-hicks@uhome:/tmp/TEST$ touch test.file
anne-hicks@uhome:/tmp/TEST$ ls -l
total 0
-rw-rw---- 1 anne-hicks leads 0 2011-02-01 15:41 test.file
anne-hicks@uhome:/tmp/TEST$ cd ..
anne-hicks@uhome:/tmp$ su - stevi-jerrold
Password:
stevi-jerrold@uhome:~$ cd /tmp/TEST
stevi-jerrold@uhome:/tmp/TEST$ touch test.file.2
stevi-jerrold@uhome:/tmp/TEST$ ls -l
total 0
-rw-rw---- 1 anne-hicks    leads 0 2011-02-01 15:41 test.file
-rw-r--r-- 1 stevi-jerrold leads 0 2011-02-01 15:42 test.file.2
stevi-jerrold@uhome:/tmp/TEST$ wtf ?
The program 'wtf' is currently not installed.  To run 'wtf' please ask your administrator to install the package 'bsdgames'
stevi-jerrold@uhome:/tmp/TEST$


Shouldn't the new file (with ower stevi-jerrold) have been created as anne-hicks ?

---

### Post by ibuclaw on 2011-02-01
Setuid only alters behaviour on executable files.

> 
SUID or setuid: change user ID on execution. If setuid bit is set, when the file will be executed by a user, the process will have the same rights as the owner of the file being executed.


The setuid permission set on a directory is ignored on Linux systems.

Regards

---

### Post by bodhi.zazen on 2011-02-01
See also :

[http://osr507doc.sco.com/en/OSAdminG/ssC.stickydirs.html](http://osr507doc.sco.com/en/OSAdminG/ssC.stickydirs.html)

---

### Post by Robx610 on 2011-02-01
At this point I think it would help to go into greater detail about my intentions. I have a leads folder owned by anne-hicks and the group leads; two other users (Stevi-jerrold & Wendi-kirchner) are also members of the leads group. All of the members of the leads group have rw access to the folder and its contents. It is also important to add that the folder is being shared via samba (the samba permissions only give initial permission to the root directory parent to the leads directory (/home/leads), after that point Linux permissions handle the rest. 

From start to finish the process is as follows: Stevi or Wendi log into their Windows PCs and move CSV files into the leads dir (via mapped drive). Then, Anne logs into a Sco Server via telnet and uses a Cobol app to run a custom written telemarketing script against the contents of the CSV (the Unix server is accessing the Linux files via NFS). The user account that Anne uses for Unix and the one she uses for Linux are different but share the same uid (no there’s no hope of consolidating servers at this time). From what I know, in order for Anne's Unix account to access the CSV stored on the Linux NFS mount, the files must be owned by Anne’s user account on Linux with the same uid as her Unix account (she cannot just be a group member on the Linux side). To clarify, if a file is owned by anne-hicks:leads, she can access it from Unix, however if it is owned by stevi-jerrold:leads, it does not work from the Unix application. Basically, Anne's group membership in Linux does not provide her Unix account with inherited permission.

I would greatly appreciate any suggestions.

---

