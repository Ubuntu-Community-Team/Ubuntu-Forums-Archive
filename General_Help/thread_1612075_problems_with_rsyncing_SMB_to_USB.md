---
title: "problems with rsyncing SMB to USB"
date: 2010-11-02
forum: General Help
---

### Post by Alan James on 2010-11-02
I need some help using rsync from the terminal. I want to make a copy of my Samba server to a local usb hard drive. I keep running into the problem that rsync only copies files to the usb server, and won't remove files that are no longer on the server.

For example I will compare two hypothetical folders together.

Contents of Folder 1:

File_01.txt		(current)
File_02.mkv		(current)
File_03.html		(current)

File_05.php		(current)

Contents of Folder 2 (before transfer)

File_01.txt		(old)
File_02.mkv		(current)
File_03.html		(old)
File_04.html		(no longer used)
File_05.php		(old)

Contents of Folder 2 (after rsync)

File_01.txt		(current)
File_02.mkv		(current)
File_03.html		(current)
File_04.html		(no longer used)
File_05.php		(current)

Now Folder 2 does not match Folder 1 because “File_04.html” has been deleted in Folder 1.

How do I fix this? I have looked on Google and searched the forum and not found an answer.

---

### Post by Alan James on 2010-11-04
Anyone have any ideas?

---

### Post by Alan James on 2010-11-06
Bump, Anyone know?

---

