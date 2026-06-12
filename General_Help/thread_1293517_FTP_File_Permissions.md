---
title: "FTP File Permissions"
date: 2009-10-17
forum: General Help
---

### Post by Majorflam on 2009-10-17
I'm running xammp. I've been downloading php scripts and assorted directories to add to my website.

The problem I'm having is that when I download the directories, they have 700 file permissions by default. I then have to chmod so the loacl server can access the files. Then, when I upload to my website using gftp, the file permissions are 700 again! I then need to chmod everything to 755 on the server.

It's time consuming and a real pain.

Is there any way I can run a command on a downloaded folder that would chmod that folder and all subfolders? Is there any way I can get gftp to then upload with the same file permissions (or can I even set new default file permissions for gftp)?

Any help much appreciated.

---

### Post by eric3_14159 on 2009-11-09
I don't know what is causing all this, it must be ftp options somewhere in the server or client, but the -R command to chmod makes it run recursively, so "chmod -R 755 ." in the directory will also act on all the files and subdirectories it contains.

In gFTP, FTP -> Options has a "Preserve File Permissions" checkbox, which may help.

---

